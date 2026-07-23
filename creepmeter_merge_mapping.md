# Creepmeter merge.bot channel mapping

_Generated 2026-07-23 by tracing `home/strain/MONITOR/CREEP/Merge1.3+` (the script `monitor_creep+` actually calls) and its `case "$site"` dispatch._ Machine-readable: [`creepmeter_merge_mapping.csv`](creepmeter_merge_mapping.csv).

Each `<site>_merge.bot` (written to `<site>_dir/`) is built from one channel's cleanstrain output (`<channel>_cl_A*.bot` + `<channel>_cl_MON.bot`), decimated to 1-day/3-day and gzipped for archive.

**Key finding**: for `type=Bil` sites, the *output* bottle name comes from the `.id` file's `Strain=` field, not from whichever raw sensor bottle is currently being read. `get_creep_chan+` writes to `$file.bot` where `$file` is the argument passed in (the Strain name) — the raw sensor it reads is column 2 of that interval's `.chan` row, which can differ. Pt Pinole is the one site where this currently diverges: output stays named **cpp1** even though the raw sensor is now **cpp3** (Hall sensor).

| site | dir | type | channel feeding merge.bot | notes |
|------|-----|------|---------------------------|-------|
| cpp | cpp_dir | Bil | cpp1 | Strain=cpp1; raw sensor currently cpp3 (Hall) per cpp.chan — get_creep_chan+ writes output AS cpp1 regardless of raw sensor name |
| coz | coz_dir | Bil | coz1 | Strain=coz1; raw sensor currently coz1 (LVDT, 2-inch range) — matches |
| ctm | ctm_dir | Bil | ctm1 | Strain=ctm1; raw sensor currently ctm1 — matches |
| chp | chp_dir | Bil | chp1 | Strain=chp1; raw sensor currently chp1 — matches |
| cfw | cfw_dir | Bil | cfw1 | Strain=cfw1; raw sensor currently cfw1 — matches |
| c46 | c46_dir | Bil | c461 | site=c46, so "$site"1 = c461 — matches Strain field |
| cfd | cfd_dir | USGS | cfwhi | classified USGS *in Merge1.3+* despite being Bil in monitor1.2+'s fetch dispatch |
| cfo | cfo_dir | USGS | cfwho | classified USGS in Merge1.3+ despite being Bil in monitor1.2+'s fetch dispatch |
| x46 | x46_dir | USGS | x461 |  |
| xgh | xgh_dir | USGS | xgh1 |  |
| crr | crr_dir | USGS | crr1 |  |
| wkr | wkr_dir | USGS | wkr1 |  |
| xta | xta_dir | USGS | xta1 |  |
| xpk | xpk_dir | USGS | xpk2 |  |
| xva | xva_dir | USGS | xva1 |  |
| xmd | xmd_dir | USGS | xmd1 |  |
| xmm | xmm_dir | USGS | xmm1 |  |
| xsc | xsc_dir | USGS | xsc1 |  |
| xmr | xmr_dir | USGS | xmr2 | strain=xmr1 then immediately overwritten to xmr2 (dead line); SPLICE: xmr1.10min.gz (pre-2018 legacy) + xmr2 data, offset currently 667mm to align trend |
| cwn | cwn_dir | USGS | cwn1 |  |
| cwp | cwp_dir | USGS | cwn2 |  |
| cwo | cwo_dir | USGS | cwn3 |  |
| cwc | cwc_dir | USGS | cwn4 |  |
| xhr | xhr_dir | USGS | xhr3 |  |
| xsj | xsj_dir | USGS | xsj3 |  |
| sjn | sjn_dir | USGS | sjnh | SPLICE: nyl_10min.dat.gz (pre-2020 Nyland archive) + sjnh data, offset -158mm for the older portion |
| xsh | xsh_dir | USGS | xshh |  |
| shl | shl_dir | USGS | xshl |  |
| sht | sht_dir | USGS | xsht |  |
| shc | shc_dir | USGS | xshco |  |
| shr | shr_dir | USGS | xshrh |  |
| xs2 | (no dir) | USGS | xshco | DEAD case entry: no xs2_dir exists; would fail at 'cd xs2_dir' if ever run — duplicate of shc |
| xsr | (no dir) | USGS | xshrh | DEAD case entry: no xsr_dir exists; duplicate of shr |
| mee | mee_dir | USGS | meed |  |
| frd | frd_dir | USGS | xfrd |  |
| fro | fro_dir | USGS | xfro |  |
| nfd | nfd_dir | USGS | xfrnd |  |
| nfo | nfo_dir | USGS | xfrno |  |
| sfr | sfr_dir | USGS | sfrd |  |
| sjb | sjb_dir | USGS | xsjd |  |
| meo | meo_dir | USGS | meeo |  |
| met | met_dir | USGS | meet |  |
| mro | mro_dir | USGS | xmro |  |
| mrc | mrc_dir | USGS | xmrc |  |
| mrt | mrt_dir | USGS | xmrt |  |

## Legacy / orphaned merge.bot files (not produced by the current Merge1.3+)

These exist on disk but the current script never writes to these exact paths — they're leftovers from earlier script versions, renamed directories, or manual snapshots:

| file | why it's orphaned |
|------|--------------------|
| `Xcwc_merge.bot`, `Xcwn_merge.bot`, `Xcwo_merge.bot`, `Xcwp_merge.bot`, `Xshc_merge.bot`, `Xshl_merge.bot`, `Xshr_merge.bot`, `Xsht_merge.bot`, `Xsjn_merge.bot`, `Xxgh_merge.bot`, `Xxhr_merge.bot`, `Xxmm_merge.bot`, `Xxmr_merge.bot`, `Xxpk_merge.bot`, `Xxsc_merge.bot`, `Xxsh_merge.bot` (top-level, capital-X prefix) | Merge1.3+ always `cd`s into `<site>_dir/` before writing — it never writes to top-level `CREEP/`. Same X-prefix backup convention seen on `Xcfw_dir/`. |
| `nrd_merge.bot`, `nro_merge.bot` (top-level) | Leftover from before the Fox Ranch-north directories were renamed `nfd_dir`/`nfo_dir` (matches the README's `nrd_dir`/`nro_dir` vs actual `nfd_dir`/`nfo_dir` naming drift noted earlier). |
| `xfrd_merge.bot` (top-level) | Duplicate of `frd_dir/xfrd_merge.bot`; not written by the current script. |
| `c46_dir/c461_merge.bot` | Coexists with the current `c46_dir/c46_merge.bot`; provenance unclear — possibly from an older Merge version, predates confirmation. |
| `shl_dir/xsl_merge.bot` | Coexists with current `shl_dir/shl_merge.bot`; matches the earlier-found duplicate `shl.chan`/`xsl.chan` naming artifact. |
| `xmr2014_dir/xmr_merge.bot` | Frozen snapshot dated 2019-08-12 (vs. the live `xmr_dir/xmr_merge.bot`, current to 2026-03-09) — a preserved pre-transition archive, not regenerated. |
