# Creepmeter channels — calibrated recent values & unit confidence

_Generated 2026-07-23; each bottle read with `usgs_bottle.py`, scaled via `.chan`/`.dat`/`.id`._ Machine-readable: [`creepmeter_calibrated.csv`](creepmeter_calibrated.csv).

- `raw` = bottle file read; `processed` = product name emitted (differ for Rupture HR/LR and `xsj2`→`xsj3`/`xpk1`→`xpk2`).
- **pipeline**: **CREEP** (`monitor_creep+`, `.chan` Bilham/Rupture) · **CREEP-USGS** (`monitor1.2+` USGS branch, `Creep_calib_140224.dat`) · **CREEP-ID** (Bilham type with no `.chan`/`.dat` entry, calibrated via its own `.id` Scale — currently only `c461`) · **Rupture-HR/LR** (`monitorR+`, 30° `1/cos`) · **raw-aux** (no monitoring pipeline).
- **available**: `true` if `processed` exactly matches a station **Code** on the USGS public download page (https://earthquake.usgs.gov/monitoring/deformation/data/download.php, verified against raw page HTML, 47 creepmeter sites). Only the primary dextral channel per site can match exactly since the page lists sites, not bottles — temp/voltage/orthogonal/CO2 channels show `false` even where the site is on the page. Fox Ranch, Mee Ranch, St Francis, and Cienega's split components don't appear on the public page at all. Includes `cpp1` (Pt Pinole's predecessor CREEP sensor, superseded by `cpp3` in 2024) and the legacy single-sensor sites `tabc`/`xmbc`/`xhsw`/`xrsw` (calibrated via `Creep_calib_140224.dat`, previously missing from this table entirely).
- `data_start`/`last_data` = bottle extent; `STALE` = no data since mid-2025. `physical` after current-interval scale; creep not offset-corrected.
- `units_confidence`: high=documented scale/unambiguous; medium=inferred integerize in range; low=placeholder/unknown/dead/misapplied scale.

## Creep — dextral / orthogonal (mm)

| station | raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|---------|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| c46 | c461 | c461 | true | CREEP-ID | dsat | dextral | 2010-12-10T00:00 | 2026-03-09T23:00 | 4467 | -53.81 | mm | high |
| c46 | c462 | c462 | false | raw-aux | dsat | dextral | 2010-12-10T00:00 | 2026-03-09T23:00 | 1713 |  | mm? | low |
| c46 | x461 | x461 | true | CREEP-USGS | dsat | dextral | 1986-10-04T05:20 | 2021-05-31T22:40 STALE | 2610.5 | 22.5 | mm | high |
| c46 | x46b | x46b | false | raw-aux | dsat | dextral2 | 1986-10-08T17:20 | 2021-05-31T22:40 STALE | 2428 |  | mm? | low |
| cfw | cfw1 | cfw1 | true | CREEP | dsat | dextral | 1993-12-07T19:00 | 2026-03-09T22:51 | 33486 | -39.18 | mm | high |
| cfw | cfw2 | cfwLR | false | Rupture-LR | dsat | dextral | 1993-12-07T19:00 | 2026-03-09T23:00 | 1872 | 58.08 | mm | high |
| cfw | cfw3 | cfwHR | false | Rupture-HR | dsat | dextral | 2011-01-26T23:10 | 2026-03-09T23:00 | 28276 | 8.718 | mm | high |
| cfw | cfwd | cfwd | false | raw-aux | dsat | dextral | 1997-05-16T18:00 | 2007-11-07T22:30 STALE | 4653 |  | mm? | low |
| cfw | cfwhi | cfwhi | false | CREEP | HOBO | dextral | 2021-12-19T21:30 | 2026-03-09T17:04 | 3.6617 | 3.662 | mm | high |
| cfw | cfwb | cfwb | false | raw-aux | dsat | dextral2 | 1993-12-07T19:00 | 2007-11-07T22:30 STALE | 4653 |  | mm? | low |
| cfw | cfwho | cfwho | false | CREEP | HOBO | orthogonal | 2021-12-09T17:49 | 2026-03-09T17:04 | 7.1751 | 7.175 | mm | high |
| chp | chp1 | chp1 | true | CREEP | dsat | dextral | 1994-04-02T01:20 | 2026-03-09T22:53 | 44277 | -52.11 | mm | high |
| chp | chp2 | chpLR | false | Rupture-LR | dsat | dextral | 1994-04-02T01:20 | 2026-03-09T23:00 | 22786 | 624.5 | mm | high |
| chp | chp3 | chpHR | false | Rupture-HR | dsat | dextral | 2014-07-27T19:40 | 2026-03-09T23:00 | 30078 | 7.686 | mm | high |
| coz | coz1 | coz1 | true | CREEP | dsat | dextral | 2007-10-19T22:10 | 2026-03-09T23:00 | 45983 | -53.69 | mm | high |
| coz | coz2 | cozLR | false | Rupture-LR | dsat | dextral | 2014-07-25T17:50 | 2026-03-09T23:00 | -6030 | -165.6 | mm | high |
| coz | coz3 | cozHR | false | Rupture-HR | dsat | dextral | 2014-07-25T17:50 | 2026-03-09T23:00 | 17806 | 4.462 | mm | high |
| cpp | cpp1 | cpp1 | true | CREEP | dsat | dextral | 1995-08-16T21:20 | 2026-03-09T22:53 | 19416 | -22.91 | mm | high |
| cpp | cpp2 | cppLR | false | Rupture-LR | dsat | dextral | 1995-08-16T21:20 | 2026-03-09T23:00 | 24576 | 679.9 | mm | high |
| cpp | cpp3 | cpp3 | false | CREEP | dsat | dextral | 2014-07-23T21:30 | 2026-03-09T23:00 | 2812 | 0.8211 | mm | high |
| cpp | cpp3 | cppHR | false | Rupture-HR | dsat | dextral | 2014-07-23T21:30 | 2026-03-09T23:00 | 2812 | 0.816 | mm | high |
| crr | crr1 | crr1 | true | CREEP-USGS | dsat | dextral | 1985-04-10T03:39 | 2021-05-31T21:09 STALE | 1714 | 21.06 | mm | high |
| ctm | ctm1 | ctm1 | true | CREEP | dsat | dextral | 2007-10-19T22:10 | 2026-03-09T22:52 | 37922 | -43.53 | mm | high |
| ctm | ctm2 | ctmLR | false | Rupture-LR | dsat | dextral | 2012-11-07T01:00 | 2026-03-09T23:00 | -8887 | -284.6 | mm | high |
| ctm | ctm3 | ctmHR | false | Rupture-HR | dsat | dextral | 2012-11-07T01:00 | 2026-03-09T23:00 | 7807 | 2.353 | mm | high |
| cwn | cwc3 | cwc3 | true | raw-aux | dsat | dextral | 1988-08-09T22:50 | 2008-05-29T20:30 STALE | 1 |  | mm? | low |
| cwn | cwn1 | cwn1 | true | CREEP-USGS | dsat | dextral | 1988-08-09T22:50 | 2023-12-21T17:32 STALE | 2172 | -2.242 | mm | high |
| cwn | cwn2 | cwn2 | false | CREEP | dsat | dextral | 2020-09-03T20:21 | 2023-12-21T17:32 STALE | 14950 | 3.279 | mm | high |
| cwn | cwn3 | cwn3 | false | CREEP | dsat | orthogonal | 2020-09-03T20:21 | 2023-12-21T17:32 STALE | 46932 | 10.28 | mm | high |
| mee | meed | meed | false | CREEP | HOBO | dextral | 2021-04-01T16:26 | 2025-05-29T23:24 STALE | 0.97204 | 0.972 | mm | high |
| mee | meeo | meeo | false | CREEP | HOBO | orthogonal | 2021-04-01T16:26 | 2025-05-29T23:24 STALE | 0.99179 | 0.9918 | mm | high |
| sfr | sf2d | sf2d | false | CREEP | HOBO | dextral | 2024-04-24T15:30 | 2026-03-09T17:17 | 8.9843 | 8.984 | mm | high |
| sfr | sf2b | sf2b | false | raw-aux | HOBO | dextral2 | 2024-04-24T15:33 | 2026-03-10T17:53 | 4.9823 |  | mm? | low |
| sfr | sf2o | sf2o | false | raw-aux | HOBO | orthogonal | 2024-04-25T05:59 | 2026-03-09T17:17 | 2.4445 |  | mm? | low |
| sjb | xsj2 | xsj3 | true | CREEP-USGS | dsat | dextral | 1988-06-15T17:50 | 2021-05-31T21:40 STALE | 1833 | 12.29 | mm | high |
| sjb | xsjd | xsjd | false | CREEP | HOBO | dextral | 2024-03-23T18:00 | 2026-03-09T16:51 | 3.7913 | 3.791 | mm | high |
| sjn | sjnh | sjnh | false | CREEP | HOBO | dextral | 2020-11-21T23:37 | 2025-02-24T21:54 STALE | 4.0559 | 4.056 | mm | high |
| sjn | sjnl | sjnl | false | raw-aux | HOBO | dextral | 2020-11-21T23:37 | 2025-02-24T21:54 STALE | 3.5517 |  | mm? | low |
| tabc | tabc | tabc | true | CREEP-USGS | dsat | dextral | 1985-12-15T22:30 | 2025-07-26T05:10 | 3439 | 212.4 | mm | high |
| wkr | wkr1 | wkr1 | true | CREEP-USGS | dsat | dextral | 1984-10-17T22:19 | 2026-03-09T22:59 | 607 | 9.16 | mm | high |
| xfr | xfrd | xfrd | false | CREEP | HOBO | dextral | 2022-06-03T00:00 | 2026-03-09T16:31 | 6.0497 | 6.05 | mm | high |
| xfr | xfrnd | xfrnd | false | CREEP | HOBO | dextral | 2025-08-01T22:02 | 2026-03-09T16:31 | 3.4582 | 3.458 | mm | high |
| xfr | xfrno | xfrno | false | CREEP | HOBO | orthogonal | 2025-08-01T22:02 | 2026-03-09T16:31 | 7.2121 | 7.212 | mm | high |
| xfr | xfro | xfro | false | CREEP | HOBO | orthogonal | 2022-06-03T00:00 | 2026-03-09T16:31 | 6.6421 | 6.642 | mm | high |
| xgh | xgh1 | xgh1 | true | CREEP-USGS | dsat | dextral | 1984-09-28T16:59 | 2022-06-28T13:09 STALE | 2491 | 16.54 | mm | high |
| xhr | xhr2 | xhr2 | true | CREEP-USGS | dsat | dextral | 2005-01-01T00:00 | 2005-11-04T14:10 STALE | -2705 | -19.05 | mm | high |
| xhr | xhr3 | xhr3 | true | CREEP-USGS | dsat | dextral | 2009-08-20T00:10 | 2026-03-09T22:51 | 7800 | 5.342 | mm | high |
| xhsw | xhsw | xhsw | true | CREEP-USGS | dsat | dextral | 1987-07-06T20:38 | 2011-07-08T02:38 STALE | 3 | 0.003375 | mm | high |
| xmbc | xmbc | xmbc | true | CREEP-USGS | dsat | dextral | 1985-09-12T22:49 | 2026-03-09T22:59 | 976 | 45.22 | mm | high |
| xmd | xmd1 | xmd1 | true | CREEP-USGS | dsat | dextral | 1986-09-19T22:19 | 2026-03-09T22:59 | 3168 | -25.85 | mm | high |
| xmd | xmdb | xmdb | false | raw-aux | dsat | dextral2 | 2006-11-29T20:10 | 2026-03-09T23:00 | 976 |  | mm? | low |
| xmm | xmm1 | xmm1 | true | CREEP-USGS | dsat | dextral | 1984-09-24T20:30 | 2026-03-09T23:00 | 2847 | 22.16 | mm | high |
| xmr | xmr1 | xmr1 | true | CREEP-USGS | dsat | dextral | 1988-06-13T14:50 | 2019-04-13T07:00 STALE | 2042.5 | 1.97 | mm | high |
| xmr | xmr2 | xmr2 | false | CREEP-USGS | dsat | dextral | 2018-09-05T23:25 | 2026-03-09T22:51 | 15457 | 3.898 | mm | high |
| xmr | xmro | xmro | false | CREEP | dsat | orthogonal | 2020-10-21T18:30 | 2026-03-09T22:51 | 23140 | 5.408 | mm | high |
| xpk | xpk1 | xpk2 | true | CREEP-USGS | dsat | dextral | 1985-08-23T16:30 | 2023-03-08T23:40 STALE | 338.5 | 2.505 | mm | high |
| xrsw | xrsw | xrsw | true | CREEP-USGS | dsat | dextral | 2005-01-01T00:00 | 2005-12-12T22:30 STALE | 2 | 0.001867 | mm | high |
| xsc | xsc1 | xsc1 | true | CREEP-USGS | dsat | dextral | 1985-04-10T03:39 | 2022-11-15T00:39 STALE | 4651 | 37.41 | mm | high |
| xsh | xshh | xshh | false | CREEP | HOBO | dextral | 2020-10-14T12:00 | 2026-03-09T17:14 | 5.8204 | 5.82 | mm | high |
| xsh | xshl | xshl | false | CREEP | HOBO | dextral | 2020-10-14T12:00 | 2026-03-09T17:14 | 87.599 | 87.6 | mm | high |
| xta | xta1 | xta1 | true | CREEP-USGS | dsat | dextral | 1985-12-15T22:30 | 2025-07-26T05:10 | 1344 | 10.67 | mm | high |
| xva | xva1 | xva1 | true | CREEP-USGS | dsat | dextral | 2006-11-28T23:10 | 2021-05-31T22:50 STALE | 0 | -58.65 | mm | high |
| xva | xvab | xvab | false | raw-aux | dsat | dextral2 | 1987-05-26T21:38 | 2021-05-31T22:58 STALE | 2583 |  | mm? | low |

## Temperature

| station | raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|---------|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| c46 | c46t | c46t | false | raw-aux | dsat | temp | 2010-12-10T00:00 | 2026-03-09T23:00 | 1255 | -15.12 | ? | low |
| cfw | cfwht | cfwht | false | raw-aux | HOBO | temp | 2021-12-08T23:36 | 2026-03-09T17:04 | 15.223 | 15.22 | degC | high |
| cfw | cfwht2 | cfwht2 | false | raw-aux | HOBO | temp | 2021-12-17T00:20 | 2026-03-09T17:04 | 14.916 | 14.92 | degC | high |
| cfw | cfwt | cfwt | false | raw-aux | dsat | temp | 1993-12-07T19:00 | 2026-03-09T23:00 | 1825 | 18.25 | degC | medium |
| chp | chpt | chpt | false | raw-aux | dsat | temp | 1994-04-02T01:20 | 2026-03-09T23:00 | 33032 | 330.3 | degC | low |
| coz | cozt | cozt | false | raw-aux | dsat | temp | 2007-10-19T22:10 | 2026-03-09T23:00 | 2050 | 20.5 | degC | medium |
| cpp | cppt | cppt | false | raw-aux | dsat | temp | 1995-08-16T21:20 | 2026-03-09T23:00 | 2742 | 27.42 | degC | medium |
| ctm | ctmt | ctmt | false | raw-aux | dsat | temp | 2007-10-19T22:10 | 2026-03-09T23:00 | 1525 | 15.25 | degC | medium |
| cwn | cwnt | cwnt | false | raw-aux | dsat | temp | 2022-04-01T01:01 | 2023-12-21T17:32 STALE | 88809 | 888.1 | degC | low |
| mee | meet | meet | false | CREEP | HOBO | temp | 2021-04-01T16:26 | 2025-05-29T23:24 STALE | 35.155 | 35.16 | degC | high |
| sfr | sf2t | sf2t | false | raw-aux | HOBO | temp | 2024-04-24T15:30 | 2026-03-09T17:17 | 11.88 | 11.88 | degC | high |
| sfr | sfrt | sfrt | false | raw-aux | HOBO | temp | 2022-11-03T11:00 | 2025-10-30T22:00 | 16.82 | 16.82 | degC | high |
| sjb | xsjt | xsjt | false | raw-aux | HOBO | temp | 2024-03-24T04:13 | 2026-03-09T16:51 | 11.929 | 11.93 | degC | high |
| sjn | sjngt | sjngt | false | raw-aux | HOBO | ground-temp | 2020-11-21T23:37 | 2024-03-25T20:36 STALE | 0.00031316 | 0.0003132 | degC | low |
| sjn | sjnt | sjnt | false | raw-aux | HOBO | temp | 2020-11-21T23:37 | 2025-02-24T21:54 STALE | 4.9909 | 4.991 | degC | low |
| xfr | xfrt | xfrt | false | raw-aux | HOBO | temp | 2022-06-03T00:00 | 2026-03-09T16:31 | 13.209 | 13.21 | degC | high |
| xmr | xmrt | xmrt | false | CREEP | dsat | temp | 2020-10-21T18:30 | 2026-03-09T22:51 | -5461 | -54.61 | degC | low |
| xsh | xshdp | xshdp | false | raw-aux | HOBO | dewpoint | 2020-10-14T12:00 | 2023-04-05T01:07 STALE | 13.466 | 13.47 | degC | medium |
| xsh | xsht | xsht | false | CREEP | HOBO | temp | 2020-10-14T12:00 | 2026-03-09T17:14 | 11.443 | 11.44 | degC | high |

## Battery / supply voltage

| station | raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|---------|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| c46 | c46v | c46v | false | raw-aux | dsat | voltage | 2010-12-10T00:00 | 2026-03-09T23:00 | 1247 | 12.47 | V | high |
| c46 | x46v | x46v | false | raw-aux | dsat | voltage | 2014-02-25T00:00 | 2021-05-31T22:40 STALE | 1270 | 12.7 | V | high |
| cfw | cfwhv | cfwhv | false | raw-aux | HOBO | voltage | 2021-12-08T23:45 | 2026-03-09T17:05 | 4.2279 | 4.228 | V | high |
| cfw | cfwv | cfwv | false | raw-aux | dsat | voltage | 2007-11-06T20:50 | 2026-03-09T23:00 | 1223 | 12.23 | V | high |
| chp | chpv | chpv | false | raw-aux | dsat | voltage | 2007-11-15T23:10 | 2026-03-09T23:00 | 1223 | 12.23 | V | high |
| coz | cozv | cozv | false | raw-aux | dsat | voltage | 2007-10-19T22:10 | 2026-03-09T23:00 | 1294 | 12.94 | V | low |
| cpp | cppv | cppv | false | raw-aux | dsat | voltage | 1997-12-24T17:50 | 2026-03-09T23:00 | 1223 | 12.23 | V | high |
| crr | crrv | crrv | false | raw-aux | dsat | voltage | 2009-09-23T16:00 | 2021-05-31T21:10 STALE | 1282 | 12.82 | V | high |
| ctm | ctmv | ctmv | false | raw-aux | dsat | voltage | 2007-10-19T22:10 | 2026-03-09T23:00 | 1247 | 12.47 | V | high |
| cwn | cwnv | cwnv | false | raw-aux | dsat | voltage | 2007-04-12T01:00 | 2023-12-21T17:40 STALE | 1317 | 13.17 | V | low |
| mee | meev | meev | false | raw-aux | HOBO | voltage | 2021-01-01T08:45 | 2025-05-29T23:25 STALE | 4.2031 | 4.203 | V | high |
| sfr | sf2v | sf2v | false | raw-aux | HOBO | voltage | 2024-04-25T14:00 | 2026-03-09T17:17 | 4.9877 | 4.988 | V | low |
| sfr | sfrv | sfrv | false | raw-aux | HOBO | voltage | 2022-11-03T11:01 | 2025-10-30T22:01 | 8.1931 | 8.193 | V | high |
| sjb | xsjv | xsjv | false | raw-aux | dsat | voltage | 2007-11-21T21:50 | 2021-05-31T21:40 STALE | 1270 | 12.7 | V | high |
| sjb | xsjv | xsjv | false | raw-aux | HOBO | voltage | 2024-03-23T18:03 | 2026-03-09T16:53 | 4.152 | 4.152 | V | high |
| sjn | sjnv1 | sjnv1 | false | raw-aux | HOBO | voltage | 2020-11-21T23:37 | 2024-04-06T01:24 STALE | 0.012213 | 0.01221 | V | low |
| sjn | sjnv2 | sjnv2 | false | raw-aux | HOBO | voltage | 2020-11-21T23:37 | 2025-02-24T21:54 STALE | 4.3068 | 4.307 | V | high |
| wkr | wkrv | wkrv | false | raw-aux | dsat | voltage | 2006-11-30T19:00 | 2026-03-09T23:00 | 1200 | 12 | V | high |
| xfr | xfrv | xfrv | false | raw-aux | HOBO | voltage | 2022-06-03T00:01 | 2026-03-09T16:31 | 92 | 92 | V | medium |
| xgh | xghv | xghv | false | raw-aux | dsat | voltage | 2006-11-30T00:20 | 2022-06-28T13:10 STALE | 1106 | 11.06 | V | high |
| xhr | xhr2v | xhr2v | false | raw-aux | dsat | voltage | 2005-01-01T00:00 | 2005-11-04T14:10 STALE | 2603.5 | 26.04 | V | high |
| xhr | xhrv | xhrv | false | raw-aux | dsat | voltage | 2009-08-20T00:10 | 2026-03-09T23:00 | 1247 | 12.47 | V | high |
| xmd | xmdv | xmdv | false | raw-aux | dsat | voltage | 2006-11-29T20:10 | 2026-03-09T23:00 | 1270 | 12.7 | V | high |
| xmm | xmmv | xmmv | false | raw-aux | dsat | voltage | 2007-05-09T00:00 | 2026-03-09T23:00 | 1270 | 12.7 | V | high |
| xmr | xmrv | xmrv | false | raw-aux | dsat | voltage | 2008-05-28T23:00 | 2026-03-09T23:00 | 1247 | 12.47 | V | high |
| xpk | xpkv | xpkv | false | raw-aux | dsat | voltage | 2006-11-28T14:00 | 2023-03-08T23:40 STALE | 1317 | 13.17 | V | high |
| xsc | xscv | xscv | false | raw-aux | dsat | voltage | 2007-01-26T18:30 | 2022-11-15T00:40 STALE | 1247 | 12.47 | V | high |
| xsh | xshv | xshv | false | raw-aux | HOBO | voltage | 2020-10-14T12:04 | 2026-03-09T17:14 | 4.1836 | 4.184 | V | high |
| xta | xtav | xtav | false | raw-aux | dsat | voltage | 2006-12-01T00:00 | 2025-07-26T05:10 | 1200 | 12 | V | high |
| xva | xvav | xvav | false | raw-aux | dsat | voltage | 2006-11-28T23:10 | 2021-05-31T22:50 STALE | 1270 | 12.7 | V | high |

## Barometric pressure

| station | raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|---------|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| cfw | cfwhp | cfwhp | false | raw-aux | HOBO | pressure | 2021-12-08T23:36 | 2026-03-09T17:04 | 1009.3 | 1009 | mbar | high |
| sfr | sf2p | sf2p | false | raw-aux | HOBO | pressure | 2025-12-06T19:53 | 2026-03-09T17:17 | 996.95 | 996.9 | mbar | high |

## CO2

| station | raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|---------|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| cfw | cfwhc | cfwhc | false | raw-aux | HOBO | CO2 | 2021-12-17T00:20 | 2026-03-09T17:04 | 2642.4 | 2642 | ppm | medium |
| cwn | cwn4 | cwn4 | false | CREEP | dsat | CO2 | 2020-09-03T20:21 | 2023-12-21T17:32 STALE | 7158.5 | 7158 | ppm | medium |
| sjn | sjnco | sjnco | false | raw-aux | HOBO | CO2 | 2020-11-21T23:37 | 2024-03-25T20:36 STALE | 0.00031316 | 0.0003132 | V(raw) | low |
| xmr | xmrc | xmrc | false | CREEP | dsat | CO2 | 2020-10-21T18:30 | 2026-03-09T22:51 | -89 | -89 | V(raw) | low |
| xsh | xshco | xshco | false | CREEP | HOBO | CO2 | 2020-10-14T12:00 | 2023-03-12T13:50 STALE | 2.3175 | 2.318 | V(raw) | low |

## Relative humidity

| station | raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|---------|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xsh | xshrh | xshrh | false | CREEP | HOBO | rel-humidity | 2020-10-14T12:00 | 2023-04-05T01:07 STALE | 100 | 100 | %RH | high |

## Rain

| station | raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|---------|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| cfw | cfwr | cfwr | false | raw-aux | dsat | rain | 1994-01-12T20:00 | 2016-04-04T01:40 STALE | 0 | 0 | mm/tips? | low |
| cpp | cppr | cppr | false | raw-aux | dsat | rain | 1995-08-16T21:20 | 2008-01-03T21:50 STALE | 26624 | 2.662e+04 | mm/tips? | low |
| mee | meer | meer | false | raw-aux | HOBO | rain | 2024-03-27T02:50 | 2025-05-29T23:24 STALE | 2.0537 | 2.054 | mm/tips? | low |
| sfr | sf2rn | sf2rn | false | raw-aux | HOBO | rain | 2025-12-06T00:00 | 2026-03-09T17:17 | 0 | 0 | mm/tips? | low |
| sfr | sfrrn | sfrrn | false | raw-aux | HOBO | rain | 2024-03-27T00:00 | 2025-10-30T22:00 | 0 | 0 | mm/tips? | low |
| sjb | xsjr | xsjr | false | raw-aux | HOBO | rain | 2024-03-24T04:13 | 2026-03-09T16:51 | 4.9917 | 4.992 | mm/tips? | low |
| xsh | xshr | xshr | false | raw-aux | HOBO | rain | 2024-03-24T02:41 | 2026-03-09T17:14 | 4.9902 | 4.99 | mm/tips? | low |

## Other / unclassified

| station | raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|---------|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| cfw | cfwy | cfwy | false | raw-aux | dsat | other | 1997-05-16T18:00 | 2007-11-07T22:30 STALE | 4653 | 4653 | ? | low |
| ctm | ctm1x | ctm1x | false | raw-aux | dsat | variant | 2007-10-19T22:10 | 2020-01-07T16:30 STALE | 3535 | 3535 | ? | low |
| ctm | ctm2x | ctm2x | false | raw-aux | dsat | variant | 2012-11-07T01:00 | 2020-01-07T16:30 STALE | 1157.5 | 1158 | ? | low |
| ctm | ctm3x | ctm3x | false | raw-aux | dsat | variant | 2012-11-07T01:00 | 2020-01-07T16:30 STALE | 1642 | 1642 | ? | low |
| ctm | ctmtx | ctmtx | false | raw-aux | dsat | variant | 2007-10-19T22:10 | 2020-01-07T16:30 STALE | 1836 | 1836 | ? | low |
| sfr | sf2bb | sf2bb | false | raw-aux | HOBO | other | 2025-12-06T00:01 | 2026-03-09T17:16 | 4.2805 | 4.281 | ? | low |
| sjb | xsj6 | xsj6 | false | raw-aux | HOBO | other | 2025-11-01T13:18 | 2026-03-09T16:51 | 4.0526 | 4.053 | ? | low |
| sjn | sjnw | sjnw | false | raw-aux | HOBO | other | 2020-11-21T23:37 | 2025-02-24T21:54 STALE | 0.0092383 | 0.009238 | ? | low |

