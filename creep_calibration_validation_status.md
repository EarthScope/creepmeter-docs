# Creepmeter calibration validation status

Snapshot of `creep.observations.corrected_value` backfill/validation coverage. See `docs/creep_iceberg_overview.md` for the full narrative (bugs found, fixes applied, methodology).

## Where we are

134 total raw channels loaded into `creep.observations`. Of those, 59 have a real calibration recipe in `creep.calibrations`; the rest (~75) are aux/backup/voltage/rain bottles that are genuinely uncalibrated by design.

| Category | Count | Status |
|---|---|---|
| **Backfilled + independently validated** against real production ground truth (`.jl` full-history files, tolerance-based join) | **43** | 99.9999–100% match: `xhr2, xmr2, c461, xfro, ctm1, xhr3, xta1, xmm1, xsc1, xmd1, xpk1, xsj2` + 30 more (`x461, cfw1, cfwhi, cfwho, chp1, coz1, crr1, cwn1-4, meed, meeo, meet, xsjd, sjnh, wkr1, xfrd, xfrnd, xfrno, xgh1, xmr1, xmrc, xmro, xmrt, xshco, xshh, xshl, xshrh, xsht, xva1`). `cpp1` sits at 95.09% — known, accepted 2020 transition-boundary blip. |
| **Backfilled, formula trusted but not independently checkable** — no ground truth exists at all | **15** | 10 Rupture channels (`cfw2/3, chp2/3, coz2/3, cpp2/3, ctm2/3`) — can't validate because the only available ground truth (`.jl`) is itself pre-angle-bug-fix and *should* mismatch ours by the known `1/cos(30°)` factor (confirmed exactly). Plus `sf2d` (partial coverage — see gap below), `tabc`, `xmbc`, `xhsw`, `xrsw` — directories are completely empty locally, no production output ever generated to check against. |
| **Investigated, deliberately left uncalibrated** | 6 | `c46t, cfwt, chpt, cozt, cppt, ctmt` — confirmed these reuse their site's strain calibration due to a real `get_creep_usgs+` bug, producing physically-impossible "temperatures" (hundreds of degrees). Correctly `NULL` per explicit decision not to launder that bug in. |
| **Not yet touched at all** | ~70 | The remaining aux/backup/voltage/rain bottles with `calibration_method=NULL` by design (never had a real calibration recipe to backfill in the first place) — full breakdown below. |

Net: 58 of 59 calibratable channels now have `corrected_value` written and are either verified correct or running on the same thoroughly-validated formula. Only `sf2d`'s pre-cutover gap (2024-04-24 → 2025-10-30, a parallel/shadow logger running before the official cutover date, undocumented in `.chan`) remains a known, unresolved coverage hole.

Two bugs found and fixed this session affect the whole calibration layer, not just individual channels: the UTC/local-timezone boundary bug in `apply_calibration.py`, and the missing multi-interval `.chan` history for CREEP-pipeline channels.

## The remaining ~70 uncalibrated channels

69 channels confirmed `calibration_method=NULL` by design (excludes the 6 temp-channel exceptions above, which are NULL by an explicit post-hoc decision rather than by original design).

### Voltage / battery monitoring (28 channels)
`INT2/100` dsat channels are raw ADC counts meant to become volts; HOBO ones are already float volts.

| station/sensor | source | sample raw | units (believed) | note |
|---|---|---|---|---|
| c46/c46v, c46/x46v | dsat | 1317 | V (÷100) | INT2/100 → battery volts |
| cfw/cfwv | dsat | 1223 | V (÷100) | |
| cfw/cfwhv | HOBO | 4.29 | V | already float volts |
| chp/chpv | dsat | 1504 | V (÷100) | |
| coz/cozv | dsat | 1340 | V (÷100) | flagged STUCK/near-rail — likely dead |
| cpp/cppv | dsat | 377 | V (÷100) | |
| crr/crrv | dsat | 1317 | V (÷100) | |
| ctm/ctmv | dsat | 1294 | V (÷100) | |
| cwn/cwnv | dsat | 2611 | V (÷100) | flagged STUCK/near-rail — likely dead |
| mee/meev | HOBO | 0.0 | V | already float volts |
| sfr/sf2v | HOBO | 4.997 | V | flagged STUCK/near-rail — likely dead |
| sfr/sfrv | HOBO | 8.42 | V | already float volts |
| sjb/xsjv (dsat) | dsat | -5581 | V (÷100) | |
| sjb/xsjv (HOBO) | HOBO | 4.137 | V | same 4-char code, different logger — `source` disambiguates |
| sjn/sjnv1, sjn/sjnv2 | HOBO | 4.99 / 12.56 | V | sjnv1 flagged STUCK |
| wkr/wkrv | dsat | 1340 | V (÷100) | |
| xfr/xfrv | HOBO | 4.32 | V | already float volts |
| xgh/xghv | dsat | 1317 | V (÷100) | |
| xhr/xhr2v, xhr/xhrv | dsat | 2535 / 1270 | V (÷100) | |
| xmd/xmdv | dsat | 1504 | V (÷100) | |
| xmm/xmmv | dsat | 1317 | V (÷100) | |
| xmr/xmrv | dsat | 1340 | V (÷100) | |
| xpk/xpkv | dsat | 1247 | V (÷100) | |
| xsc/xscv | dsat | 1270 | V (÷100) | |
| xsh/xshv | HOBO | 8.21 | V | already float volts |
| xta/xtav | dsat | 1270 | V (÷100) | |
| xva/xvav | dsat | 1270 | V (÷100) | |

### Temperature (8 channels)
All HOBO firmware-native float °C, except one flagged-implausible dsat channel.

| station/sensor | source | sample raw | units (believed) | note |
|---|---|---|---|---|
| cfw/cfwht, cfw/cfwht2 | HOBO | 14.36 / 1.31 | degC | float degC as-stored |
| cwn/cwnt | dsat | 121636 | degC?? | manifest itself flags "degC*100 implausible 888C; encoding unknown" — genuinely unresolved, low confidence |
| sfr/sf2t, sfr/sfrt | HOBO | 16.13 / 12.61 | degC | float degC as-stored |
| sjb/xsjt | HOBO | 13.38 | degC | float degC as-stored |
| sjn/sjngt | HOBO | 1.87 | degC | labeled "ground-temp"; flagged STUCK/near-rail |
| sjn/sjnt | HOBO | 0.71 | degC | flagged STUCK/near-rail |
| xfr/xfrt | HOBO | 29.59 | degC | float degC as-stored |

### Rain gauges (7 channels)
All unverified tip-count encoding — none confirmed as real mm/tip conversion.

| station/sensor | source | sample raw | units (believed) |
|---|---|---|---|
| cfw/cfwr | dsat | 10240 | mm/tips? (unverified) |
| cpp/cppr | dsat | 0.0 | mm/tips? (unverified) |
| mee/meer | HOBO | 5.00 | mm/tips? (unverified) |
| sfr/sf2rn, sfr/sfrrn | HOBO | 0.0 / 0.0 | mm/tips? (unverified) |
| sjb/xsjr | HOBO | 5.05 | mm/tips? (unverified) |
| xsh/xshr | HOBO | 5.00 | mm/tips? (unverified) |

### Backup/secondary strain bottles — physically real slip sensors, just never calibrated (9 channels)
These are actual dextral/orthogonal displacement sensors (same physical quantity as the calibrated primary channels), but no `.chan` scale exists for them — genuinely a "could calibrate if we found the scale" gap, not aux data.

| station/sensor | source | sample raw | component | note |
|---|---|---|---|---|
| c46/c462 | dsat | 286 | dextral | secondary/backup bottle, no calibration |
| c46/x46b | dsat | 621 | dextral2 | secondary/backup bottle, no calibration |
| cfw/cfwd | dsat | 221 | dextral | no `.chan` scale for this bottle |
| cfw/cfwb | dsat | 1328 | dextral2 | secondary/backup bottle, no calibration |
| sfr/sf2b | HOBO | 4.30 | dextral2 | secondary/backup; flagged STUCK — likely dead |
| sfr/sf2o | HOBO | 0.0009 | orthogonal | no `.chan` scale for this bottle |
| sjn/sjnl | HOBO | 3.75 | dextral | no `.chan` scale for this bottle |
| xmd/xmdb | dsat | 1617 | dextral2 | secondary/backup bottle, no calibration |
| xva/xvab | dsat | 2902 | dextral2 | secondary/backup bottle, no calibration |

### Pressure / CO2 / dewpoint (5 channels)

| station/sensor | source | sample raw | component | units (believed) |
|---|---|---|---|---|
| cfw/cfwhp | HOBO | 1003.95 | pressure | mbar |
| sfr/sf2p | HOBO | 1005.45 | pressure | mbar |
| cfw/cfwhc | HOBO | 0.59 | CO2 | ppm (soil CO2, by range) |
| sjn/sjnco | HOBO | 3.81 | CO2 | stored as volts, needs ×1000 ppm/V; flagged STUCK — likely dead |
| xsh/xshdp | HOBO | 8.71 | dewpoint | degC (assumed by range) |

### Unclassified / unknown (12 channels)
No confident guess at all — manifest marks these `low` confidence, `?` units.

| station/sensor | source | sample raw | note |
|---|---|---|---|
| cfw/cfwy | dsat | 0.0 | unclassified |
| ctm/ctm1x, ctm2x, ctm3x, ctmtx | dsat | 2330 / 145 / 2306 / 1280 | unclassified "variant" bottles |
| cwn/cwc3 | dsat | 10568 | orphaned raw bottle (1988-2008), no derived files reference it at all — likely decommissioned before the site's CO2 repurposing |
| sfr/sf2bb | HOBO | 4.30 | unclassified |
| sjb/xsj6 | HOBO | 3.79 | unclassified |
| sjn/sjnw | HOBO | 0.74 | unclassified; flagged STUCK — likely dead |

**Bottom line**: of these 69, only the 9 "backup strain bottles" are physically the same kind of measurement as our calibrated channels (a genuine displacement sensor missing its `.chan` scale) — everything else is aux telemetry (voltage, rain, temp, pressure, CO2) that was never meant to produce a "mm of slip" value in the first place, correctly left uncalibrated by design.
