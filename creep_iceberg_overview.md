# Creepmeter Iceberg archive — reference

Six tables, AWS Glue catalog `creep_dev_iceberg`, `dev` profile, account `599637926940`, region `us-east-2`, warehouse `s3://creep-dev-iceberg-599637926940-us-east-2/creep`. Schemas are defined in `etl/catalog.py` (pyiceberg has no SQL DDL executor) and mirrored for humans in `docs/creep_<table>.iceberg.sql` — the two must be kept in sync by hand.

For the full design history, bugs found, and rationale behind every decision below, see **`docs/creep_iceberg_details.md`**. This doc is deliberately just "what's here and how to query it" — update it whenever a table/column is added, renamed, or dropped; leave the narrative/history to `creep_iceberg_details.md`.

## Identity model

Every table keys on **`(site, channel, source)`**:
- `site` — the station (directory), e.g. `xta`, `cpp`, `sjb`.
- `channel` — the raw sensor/bottle identity, e.g. `xta1`, `cpp1`. NOT the directory name — a directory can house more than one channel over time (see `channel_map`).
- `source` — `dsat | HOBO`, disambiguates the rare case where `(site, channel)` alone isn't unique (two different physical loggers sharing a 4-char code).

## Tables

### `creep.observations` — 173,193,321 rows
Raw bottle readings plus each derived pipeline stage, one row per sample.

| column | type | notes |
|---|---|---|
| site, channel, source | string | identity, see above |
| timestamp | timestamp | sample time |
| raw_value | float | sensor counts or logger volts |
| raw_units | string | |
| calibrated_value | double, nullable | raw_value with calibration + fixit_script edits applied |
| calibrated_units | string, nullable | |
| edited_value | double, nullable | calibrated_value with cumulative creep.edits offsets applied (all edit_source values) — **not yet populated**, needs offset-detection runs |
| qc_status | string | `ok \| excluded \| unprocessed` |
| merged_value | double, nullable | edited_value × rescale — **not yet populated**, needs edited_value first |

Partitioned by `(years(timestamp), site)`. Sparse: rows equal to the source's own missing-data sentinel are dropped at load, not stored.

### `creep.calibrations` — 184 rows
The scale/offset/angle recipe used to compute `calibrated_value` from `raw_value`. One row per real interval — a channel with N historical recalibrations has N rows.

| column | type | notes |
|---|---|---|
| calibration_id | string | natural key: `site:channel:source:calibration_method:effective_start` |
| site, channel, source | string | |
| effective_start, effective_end | timestamp | effective_end null = open-ended |
| calibration_method | string, nullable | `CREEP \| CREEP-USGS \| CREEP-ID \| Rupture`, null = uncalibrated |
| scale_value, scale_units | double/string, nullable | null when calibration_method is null |
| offset_mm, angle_deg, angle_applied | | Rupture-specific |
| source_file, source_ref, note | string | provenance |

### `creep.edits` — 1,493 rows
Every `.off` (offset event) / `.edit` (delete interval) entry, plus hardcoded "fixit" script patches and (eventually) algorithmically-detected offsets.

| column | type | notes |
|---|---|---|
| dir_stem | string | original directory stem, e.g. `cfw` — provenance only |
| site, channel, source | string | **resolved** identity, matches observations/calibrations directly (no channel_map join needed) |
| pipeline | string | `CREEP \| Rupture` — which directory tree, not a calibration concept |
| kind | string | `offset \| delete` |
| flag | string | `N`=instrumental, `T`=eq/tide, `M`=manual |
| applied | boolean | false if skipped (leading `S`) |
| event_start, event_end | timestamp | event_end only for `kind=delete` |
| note, category, source_file | string | |
| edit_source | string | `off_edit_file \| fixit_script \| cleanstrain_offset` |
| apply_stage | string | `calibrated_mm \| raw_counts` — whether magnitude applies before or after calibration |
| magnitude | double, nullable | set for `fixit_script`/`cleanstrain_offset`; null for `off_edit_file` (real offset size only known via offset estimation) |
| detection_run_id | string, nullable | `creep.offset_runs.run_id` that proposed this edit; only set for `edit_source=cleanstrain_offset` |

### `creep.channel_map` — 56 rows
Audit trail of how each `dir_stem` resolves to `(site, channel, source)` — no longer needed at query time (edits already carries resolved identity) but documents *how* ambiguous cases were decided.

| column | type | notes |
|---|---|---|
| dir_stem | string | matches creep.edits.dir_stem |
| site, channel, source | string | resolved identity |
| effective_start, effective_end | timestamp, nullable | lets one dir_stem resolve to different channels over time |
| resolution_method | string | how this row was decided |
| note | string | |

### `creep.offset_runs` — 0 rows (schema only, not yet populated)
Audit trail for offset-detection ("cleanstrain-equivalent") runs that will produce `edited_value`.

| column | type | notes |
|---|---|---|
| run_id | string | natural key: `site:channel:source:mode:window_end` |
| site, channel, source | string | |
| mode | string | `fresh` (unchained, ≤720-day window) \| `chained` (`-R` off a prior fresh run) |
| window_start, window_end, run_at | timestamp | |
| prior_run_id | string, nullable | links a chained run to the fresh run it referenced |
| white_noise, power_law_index, power_law_amplitude | double, nullable | noise-model parameters |
| results_uri | string, nullable | S3 path to raw run output |
| status | string | `ok \| failed` |
| note | string, nullable | |

### `creep.rescale_factors` — 19 rows
LVDT-aging correction (interval-scoped scale factor) needed for `merged_value`. A separate table from `calibrations` on purpose — same shape, different pipeline stage (corrects `edited_value`, not raw counts/volts). Only 9 channels have real entries.

| column | type | notes |
|---|---|---|
| rescale_id | string | natural key: `site:channel:source:effective_start` |
| site, channel, source | string | |
| effective_start, effective_end | timestamp | effective_end null = open-ended |
| old_scale_factor, new_scale_factor | double | lvdt mm/V, verbatim from source file |
| ratio | double | new/old; 1.0 = no-op interval |
| source_file, note | string | |

## Basic usage

Load a table:
```python
from catalog import get_catalog
catalog = get_catalog()
table = catalog.load_table("creep.observations")
df = table.scan(row_filter="site == 'xta' AND channel == 'xta1'").to_arrow().to_pandas()
```

Join `observations` to its calibration (interval lookup, not a flat join — pick the row whose `[effective_start, effective_end)` covers the sample's `timestamp`):
```sql
SELECT o.*, c.scale_value, c.calibration_method
FROM creep.observations o JOIN creep.calibrations c
  ON o.site = c.site AND o.channel = c.channel AND o.source = c.source
 AND o.timestamp >= c.effective_start
 AND (c.effective_end IS NULL OR o.timestamp < c.effective_end)
```

Flag samples inside an applied delete window:
```sql
SELECT o.* FROM creep.observations o LEFT JOIN creep.edits e
  ON e.site = o.site AND e.channel = o.channel AND e.source = o.source
 AND e.kind = 'delete' AND e.applied
 AND o.timestamp BETWEEN e.event_start AND e.event_end
WHERE e.channel IS NULL;   -- clean samples only
```

Backfilling: `etl/backfill_calibrated.py <site> <channel> <source>` computes `calibrated_value`/`calibrated_units` for one channel, full history. No equivalent script yet for `edited_value`/`merged_value` — those need the offset-detection run orchestration (`creep.offset_runs`) built first.

AWS SSO note: `dev` profile sessions are short-lived and expire mid-session often — `aws sso login --profile dev` to refresh.
