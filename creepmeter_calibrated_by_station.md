# Creepmeter channels by station

_Generated 2026-07-23 from [`creepmeter_calibrated.csv`](creepmeter_calibrated.csv)._ Same data as [`creepmeter_calibrated.md`](creepmeter_calibrated.md), **grouped by station**.

- `raw` = bottle read; `processed` = product name (differ for Rupture HR/LR and `xsj2`→`xsj3`/`xpk1`→`xpk2`).
- **pipeline**: **CREEP** (`monitor_creep+`, `.chan` Bilham/Rupture) · **CREEP-USGS** (`monitor1.2+` USGS branch, `Creep_calib_140224.dat`) · **CREEP-ID** (Bilham type with no `.chan`/`.dat` entry, calibrated via its own `.id` Scale — currently only `c461`) · **Rupture-HR/LR** (`monitorR+`, 30° `1/cos`) · **raw-aux** (no monitoring pipeline).
- **available**: `true` if `processed` exactly matches a station **Code** on the USGS public download page (https://earthquake.usgs.gov/monitoring/deformation/data/download.php, verified against raw page HTML, 47 creepmeter sites). Only the primary dextral channel per site can match exactly since the page lists sites, not bottles — temp/voltage/orthogonal/CO2 channels show `false` even where the site is on the page. Fox Ranch, Mee Ranch, St Francis, and Cienega's split components don't appear on the public page at all. Includes `cpp1` (Pt Pinole's predecessor CREEP sensor, superseded by `cpp3` in 2024) and the legacy single-sensor sites `tabc`/`xmbc`/`xhsw`/`xrsw` (calibrated via `Creep_calib_140224.dat`, previously missing from this table entirely).
- `data_start`/`last_data` = bottle extent; `STALE` = no data since mid-2025; creep scaled not offset-corrected.

## c46 — Highway 46 (Parkfield)

_7 channels (4 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| c461 | c461 | true | CREEP-ID | dsat | dextral | 2010-12-10T00:00 | 2026-03-09T23:00 | 4467 | -53.81 | mm | high |
| x461 | x461 | true | CREEP-USGS | dsat | dextral | 1986-10-04T05:20 | 2021-05-31T22:40 STALE | 2610.5 | 22.5 | mm | high |
| c462 | c462 | false | raw-aux | dsat | dextral | 2010-12-10T00:00 | 2026-03-09T23:00 | 1713 |  | mm? | low |
| x46b | x46b | false | raw-aux | dsat | dextral2 | 1986-10-08T17:20 | 2021-05-31T22:40 STALE | 2428 |  | mm? | low |
| c46t | c46t | false | raw-aux | dsat | temp | 2010-12-10T00:00 | 2026-03-09T23:00 | 1255 | -15.12 | ? | low |
| c46v | c46v | false | raw-aux | dsat | voltage | 2010-12-10T00:00 | 2026-03-09T23:00 | 1247 | 12.47 | V | high |
| x46v | x46v | false | raw-aux | dsat | voltage | 2014-02-25T00:00 | 2021-05-31T22:40 STALE | 1270 | 12.7 | V | high |

## cfw — Fremont Winery (Hayward)

_16 channels (12 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| cfw1 | cfw1 | true | CREEP | dsat | dextral | 1993-12-07T19:00 | 2026-03-09T22:51 | 33486 | -39.18 | mm | high |
| cfwhi | cfwhi | false | CREEP | HOBO | dextral | 2021-12-19T21:30 | 2026-03-09T17:04 | 3.6617 | 3.662 | mm | high |
| cfw3 | cfwHR | false | Rupture-HR | dsat | dextral | 2011-01-26T23:10 | 2026-03-09T23:00 | 28276 | 8.718 | mm | high |
| cfw2 | cfwLR | false | Rupture-LR | dsat | dextral | 1993-12-07T19:00 | 2026-03-09T23:00 | 1872 | 58.08 | mm | high |
| cfwd | cfwd | false | raw-aux | dsat | dextral | 1997-05-16T18:00 | 2007-11-07T22:30 STALE | 4653 |  | mm? | low |
| cfwb | cfwb | false | raw-aux | dsat | dextral2 | 1993-12-07T19:00 | 2007-11-07T22:30 STALE | 4653 |  | mm? | low |
| cfwho | cfwho | false | CREEP | HOBO | orthogonal | 2021-12-09T17:49 | 2026-03-09T17:04 | 7.1751 | 7.175 | mm | high |
| cfwht | cfwht | false | raw-aux | HOBO | temp | 2021-12-08T23:36 | 2026-03-09T17:04 | 15.223 | 15.22 | degC | high |
| cfwht2 | cfwht2 | false | raw-aux | HOBO | temp | 2021-12-17T00:20 | 2026-03-09T17:04 | 14.916 | 14.92 | degC | high |
| cfwt | cfwt | false | raw-aux | dsat | temp | 1993-12-07T19:00 | 2026-03-09T23:00 | 1825 | 18.25 | degC | medium |
| cfwhp | cfwhp | false | raw-aux | HOBO | pressure | 2021-12-08T23:36 | 2026-03-09T17:04 | 1009.3 | 1009 | mbar | high |
| cfwhv | cfwhv | false | raw-aux | HOBO | voltage | 2021-12-08T23:45 | 2026-03-09T17:05 | 4.2279 | 4.228 | V | high |
| cfwv | cfwv | false | raw-aux | dsat | voltage | 2007-11-06T20:50 | 2026-03-09T23:00 | 1223 | 12.23 | V | high |
| cfwhc | cfwhc | false | raw-aux | HOBO | CO2 | 2021-12-17T00:20 | 2026-03-09T17:04 | 2642.4 | 2642 | ppm | medium |
| cfwr | cfwr | false | raw-aux | dsat | rain | 1994-01-12T20:00 | 2016-04-04T01:40 STALE | 0 | 0 | mm/tips? | low |
| cfwy | cfwy | false | raw-aux | dsat | other | 1997-05-16T18:00 | 2007-11-07T22:30 STALE | 4653 | 4653 | ? | low |

## chp — Hayward Palisades

_5 channels (5 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| chp1 | chp1 | true | CREEP | dsat | dextral | 1994-04-02T01:20 | 2026-03-09T22:53 | 44277 | -52.11 | mm | high |
| chp3 | chpHR | false | Rupture-HR | dsat | dextral | 2014-07-27T19:40 | 2026-03-09T23:00 | 30078 | 7.686 | mm | high |
| chp2 | chpLR | false | Rupture-LR | dsat | dextral | 1994-04-02T01:20 | 2026-03-09T23:00 | 22786 | 624.5 | mm | high |
| chpt | chpt | false | raw-aux | dsat | temp | 1994-04-02T01:20 | 2026-03-09T23:00 | 33032 | 330.3 | degC | low |
| chpv | chpv | false | raw-aux | dsat | voltage | 2007-11-15T23:10 | 2026-03-09T23:00 | 1223 | 12.23 | V | high |

## coz — Oakland Zoo (Hayward)

_5 channels (5 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| coz1 | coz1 | true | CREEP | dsat | dextral | 2007-10-19T22:10 | 2026-03-09T23:00 | 45983 | -53.69 | mm | high |
| coz3 | cozHR | false | Rupture-HR | dsat | dextral | 2014-07-25T17:50 | 2026-03-09T23:00 | 17806 | 4.462 | mm | high |
| coz2 | cozLR | false | Rupture-LR | dsat | dextral | 2014-07-25T17:50 | 2026-03-09T23:00 | -6030 | -165.6 | mm | high |
| cozt | cozt | false | raw-aux | dsat | temp | 2007-10-19T22:10 | 2026-03-09T23:00 | 2050 | 20.5 | degC | medium |
| cozv | cozv | false | raw-aux | dsat | voltage | 2007-10-19T22:10 | 2026-03-09T23:00 | 1294 | 12.94 | V | low |

## cpp — Pt Pinole (Hayward)

_7 channels (6 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| cpp1 | cpp1 | true | CREEP | dsat | dextral | 1995-08-16T21:20 | 2026-03-09T22:53 | 19416 | -22.91 | mm | high |
| cpp3 | cpp3 | false | CREEP | dsat | dextral | 2014-07-23T21:30 | 2026-03-09T23:00 | 2812 | 0.8211 | mm | high |
| cpp3 | cppHR | false | Rupture-HR | dsat | dextral | 2014-07-23T21:30 | 2026-03-09T23:00 | 2812 | 0.816 | mm | high |
| cpp2 | cppLR | false | Rupture-LR | dsat | dextral | 1995-08-16T21:20 | 2026-03-09T23:00 | 24576 | 679.9 | mm | high |
| cppt | cppt | false | raw-aux | dsat | temp | 1995-08-16T21:20 | 2026-03-09T23:00 | 2742 | 27.42 | degC | medium |
| cppv | cppv | false | raw-aux | dsat | voltage | 1997-12-24T17:50 | 2026-03-09T23:00 | 1223 | 12.23 | V | high |
| cppr | cppr | false | raw-aux | dsat | rain | 1995-08-16T21:20 | 2008-01-03T21:50 STALE | 26624 | 2.662e+04 | mm/tips? | low |

## crr — Carr Ranch (Parkfield)

_2 channels (0 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| crr1 | crr1 | true | CREEP-USGS | dsat | dextral | 1985-04-10T03:39 | 2021-05-31T21:09 STALE | 1714 | 21.06 | mm | high |
| crrv | crrv | false | raw-aux | dsat | voltage | 2009-09-23T16:00 | 2021-05-31T21:10 STALE | 1282 | 12.82 | V | high |

## ctm — Temescal (Hayward)

_9 channels (5 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| ctm1 | ctm1 | true | CREEP | dsat | dextral | 2007-10-19T22:10 | 2026-03-09T22:52 | 37922 | -43.53 | mm | high |
| ctm3 | ctmHR | false | Rupture-HR | dsat | dextral | 2012-11-07T01:00 | 2026-03-09T23:00 | 7807 | 2.353 | mm | high |
| ctm2 | ctmLR | false | Rupture-LR | dsat | dextral | 2012-11-07T01:00 | 2026-03-09T23:00 | -8887 | -284.6 | mm | high |
| ctmt | ctmt | false | raw-aux | dsat | temp | 2007-10-19T22:10 | 2026-03-09T23:00 | 1525 | 15.25 | degC | medium |
| ctmv | ctmv | false | raw-aux | dsat | voltage | 2007-10-19T22:10 | 2026-03-09T23:00 | 1247 | 12.47 | V | high |
| ctm1x | ctm1x | false | raw-aux | dsat | variant | 2007-10-19T22:10 | 2020-01-07T16:30 STALE | 3535 | 3535 | ? | low |
| ctm2x | ctm2x | false | raw-aux | dsat | variant | 2012-11-07T01:00 | 2020-01-07T16:30 STALE | 1157.5 | 1158 | ? | low |
| ctm3x | ctm3x | false | raw-aux | dsat | variant | 2012-11-07T01:00 | 2020-01-07T16:30 STALE | 1642 | 1642 | ? | low |
| ctmtx | ctmtx | false | raw-aux | dsat | variant | 2007-10-19T22:10 | 2020-01-07T16:30 STALE | 1836 | 1836 | ? | low |

## cwn — Cienega Winery (San Juan SAF)

_7 channels (0 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| cwn2 | cwn2 | false | CREEP | dsat | dextral | 2020-09-03T20:21 | 2023-12-21T17:32 STALE | 14950 | 3.279 | mm | high |
| cwn1 | cwn1 | true | CREEP-USGS | dsat | dextral | 1988-08-09T22:50 | 2023-12-21T17:32 STALE | 2172 | -2.242 | mm | high |
| cwc3 | cwc3 | true | raw-aux | dsat | dextral | 1988-08-09T22:50 | 2008-05-29T20:30 STALE | 1 |  | mm? | low |
| cwn3 | cwn3 | false | CREEP | dsat | orthogonal | 2020-09-03T20:21 | 2023-12-21T17:32 STALE | 46932 | 10.28 | mm | high |
| cwnt | cwnt | false | raw-aux | dsat | temp | 2022-04-01T01:01 | 2023-12-21T17:32 STALE | 88809 | 888.1 | degC | low |
| cwnv | cwnv | false | raw-aux | dsat | voltage | 2007-04-12T01:00 | 2023-12-21T17:40 STALE | 1317 | 13.17 | V | low |
| cwn4 | cwn4 | false | CREEP | dsat | CO2 | 2020-09-03T20:21 | 2023-12-21T17:32 STALE | 7158.5 | 7158 | ppm | medium |

## mee — Mee Ranch (SAF)

_5 channels (0 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| meed | meed | false | CREEP | HOBO | dextral | 2021-04-01T16:26 | 2025-05-29T23:24 STALE | 0.97204 | 0.972 | mm | high |
| meeo | meeo | false | CREEP | HOBO | orthogonal | 2021-04-01T16:26 | 2025-05-29T23:24 STALE | 0.99179 | 0.9918 | mm | high |
| meet | meet | false | CREEP | HOBO | temp | 2021-04-01T16:26 | 2025-05-29T23:24 STALE | 35.155 | 35.16 | degC | high |
| meev | meev | false | raw-aux | HOBO | voltage | 2021-01-01T08:45 | 2025-05-29T23:25 STALE | 4.2031 | 4.203 | V | high |
| meer | meer | false | raw-aux | HOBO | rain | 2024-03-27T02:50 | 2025-05-29T23:24 STALE | 2.0537 | 2.054 | mm/tips? | low |

## sfr — St Francis (San Juan SAF)

_11 channels (11 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| sf2d | sf2d | false | CREEP | HOBO | dextral | 2024-04-24T15:30 | 2026-03-09T17:17 | 8.9843 | 8.984 | mm | high |
| sf2b | sf2b | false | raw-aux | HOBO | dextral2 | 2024-04-24T15:33 | 2026-03-10T17:53 | 4.9823 |  | mm? | low |
| sf2o | sf2o | false | raw-aux | HOBO | orthogonal | 2024-04-25T05:59 | 2026-03-09T17:17 | 2.4445 |  | mm? | low |
| sf2t | sf2t | false | raw-aux | HOBO | temp | 2024-04-24T15:30 | 2026-03-09T17:17 | 11.88 | 11.88 | degC | high |
| sfrt | sfrt | false | raw-aux | HOBO | temp | 2022-11-03T11:00 | 2025-10-30T22:00 | 16.82 | 16.82 | degC | high |
| sf2p | sf2p | false | raw-aux | HOBO | pressure | 2025-12-06T19:53 | 2026-03-09T17:17 | 996.95 | 996.9 | mbar | high |
| sf2v | sf2v | false | raw-aux | HOBO | voltage | 2024-04-25T14:00 | 2026-03-09T17:17 | 4.9877 | 4.988 | V | low |
| sfrv | sfrv | false | raw-aux | HOBO | voltage | 2022-11-03T11:01 | 2025-10-30T22:01 | 8.1931 | 8.193 | V | high |
| sf2rn | sf2rn | false | raw-aux | HOBO | rain | 2025-12-06T00:00 | 2026-03-09T17:17 | 0 | 0 | mm/tips? | low |
| sfrrn | sfrrn | false | raw-aux | HOBO | rain | 2024-03-27T00:00 | 2025-10-30T22:00 | 0 | 0 | mm/tips? | low |
| sf2bb | sf2bb | false | raw-aux | HOBO | other | 2025-12-06T00:01 | 2026-03-09T17:16 | 4.2805 | 4.281 | ? | low |

## sjb — San Juan Bautista

_7 channels (5 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xsjd | xsjd | false | CREEP | HOBO | dextral | 2024-03-23T18:00 | 2026-03-09T16:51 | 3.7913 | 3.791 | mm | high |
| xsj2 | xsj3 | true | CREEP-USGS | dsat | dextral | 1988-06-15T17:50 | 2021-05-31T21:40 STALE | 1833 | 12.29 | mm | high |
| xsjt | xsjt | false | raw-aux | HOBO | temp | 2024-03-24T04:13 | 2026-03-09T16:51 | 11.929 | 11.93 | degC | high |
| xsjv | xsjv | false | raw-aux | dsat | voltage | 2007-11-21T21:50 | 2021-05-31T21:40 STALE | 1270 | 12.7 | V | high |
| xsjv | xsjv | false | raw-aux | HOBO | voltage | 2024-03-23T18:03 | 2026-03-09T16:53 | 4.152 | 4.152 | V | high |
| xsjr | xsjr | false | raw-aux | HOBO | rain | 2024-03-24T04:13 | 2026-03-09T16:51 | 4.9917 | 4.992 | mm/tips? | low |
| xsj6 | xsj6 | false | raw-aux | HOBO | other | 2025-11-01T13:18 | 2026-03-09T16:51 | 4.0526 | 4.053 | ? | low |

## sjn — San Juan Nyland

_8 channels (0 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| sjnh | sjnh | false | CREEP | HOBO | dextral | 2020-11-21T23:37 | 2025-02-24T21:54 STALE | 4.0559 | 4.056 | mm | high |
| sjnl | sjnl | false | raw-aux | HOBO | dextral | 2020-11-21T23:37 | 2025-02-24T21:54 STALE | 3.5517 |  | mm? | low |
| sjnt | sjnt | false | raw-aux | HOBO | temp | 2020-11-21T23:37 | 2025-02-24T21:54 STALE | 4.9909 | 4.991 | degC | low |
| sjngt | sjngt | false | raw-aux | HOBO | ground-temp | 2020-11-21T23:37 | 2024-03-25T20:36 STALE | 0.00031316 | 0.0003132 | degC | low |
| sjnv1 | sjnv1 | false | raw-aux | HOBO | voltage | 2020-11-21T23:37 | 2024-04-06T01:24 STALE | 0.012213 | 0.01221 | V | low |
| sjnv2 | sjnv2 | false | raw-aux | HOBO | voltage | 2020-11-21T23:37 | 2025-02-24T21:54 STALE | 4.3068 | 4.307 | V | high |
| sjnco | sjnco | false | raw-aux | HOBO | CO2 | 2020-11-21T23:37 | 2024-03-25T20:36 STALE | 0.00031316 | 0.0003132 | V(raw) | low |
| sjnw | sjnw | false | raw-aux | HOBO | other | 2020-11-21T23:37 | 2025-02-24T21:54 STALE | 0.0092383 | 0.009238 | ? | low |

## tabc — Taylor Ranch; Big Creep (Parkfield)

_1 channels (1 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| tabc | tabc | true | CREEP-USGS | dsat | dextral | 1985-12-15T22:30 | 2025-07-26T05:10 | 3439 | 212.4 | mm | high |

## wkr — Work Ranch (Parkfield)

_2 channels (2 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| wkr1 | wkr1 | true | CREEP-USGS | dsat | dextral | 1984-10-17T22:19 | 2026-03-09T22:59 | 607 | 9.16 | mm | high |
| wkrv | wkrv | false | raw-aux | dsat | voltage | 2006-11-30T19:00 | 2026-03-09T23:00 | 1200 | 12 | V | high |

## xfr — Fox Ranch (San Juan SAF)

_6 channels (6 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xfrd | xfrd | false | CREEP | HOBO | dextral | 2022-06-03T00:00 | 2026-03-09T16:31 | 6.0497 | 6.05 | mm | high |
| xfrnd | xfrnd | false | CREEP | HOBO | dextral | 2025-08-01T22:02 | 2026-03-09T16:31 | 3.4582 | 3.458 | mm | high |
| xfrno | xfrno | false | CREEP | HOBO | orthogonal | 2025-08-01T22:02 | 2026-03-09T16:31 | 7.2121 | 7.212 | mm | high |
| xfro | xfro | false | CREEP | HOBO | orthogonal | 2022-06-03T00:00 | 2026-03-09T16:31 | 6.6421 | 6.642 | mm | high |
| xfrt | xfrt | false | raw-aux | HOBO | temp | 2022-06-03T00:00 | 2026-03-09T16:31 | 13.209 | 13.21 | degC | high |
| xfrv | xfrv | false | raw-aux | HOBO | voltage | 2022-06-03T00:01 | 2026-03-09T16:31 | 92 | 92 | V | medium |

## xgh — Gold Hill (Parkfield)

_2 channels (0 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xgh1 | xgh1 | true | CREEP-USGS | dsat | dextral | 1984-09-28T16:59 | 2022-06-28T13:09 STALE | 2491 | 16.54 | mm | high |
| xghv | xghv | false | raw-aux | dsat | voltage | 2006-11-30T00:20 | 2022-06-28T13:10 STALE | 1106 | 11.06 | V | high |

## xhr — Harris Ranch

_4 channels (2 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xhr2 | xhr2 | true | CREEP-USGS | dsat | dextral | 2005-01-01T00:00 | 2005-11-04T14:10 STALE | -2705 | -19.05 | mm | high |
| xhr3 | xhr3 | true | CREEP-USGS | dsat | dextral | 2009-08-20T00:10 | 2026-03-09T22:51 | 7800 | 5.342 | mm | high |
| xhr2v | xhr2v | false | raw-aux | dsat | voltage | 2005-01-01T00:00 | 2005-11-04T14:10 STALE | 2603.5 | 26.04 | V | high |
| xhrv | xhrv | false | raw-aux | dsat | voltage | 2009-08-20T00:10 | 2026-03-09T23:00 | 1247 | 12.47 | V | high |

## xhsw — Hearst, SW trace (Parkfield)

_1 channels (0 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xhsw | xhsw | true | CREEP-USGS | dsat | dextral | 1987-07-06T20:38 | 2011-07-08T02:38 STALE | 3 | 0.003375 | mm | high |

## xmbc — Middle Mtn; Big Creep (Parkfield)

_1 channels (1 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xmbc | xmbc | true | CREEP-USGS | dsat | dextral | 1985-09-12T22:49 | 2026-03-09T22:59 | 976 | 45.22 | mm | high |

## xmd — Middle Ridge (Parkfield)

_3 channels (3 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xmd1 | xmd1 | true | CREEP-USGS | dsat | dextral | 1986-09-19T22:19 | 2026-03-09T22:59 | 3168 | -25.85 | mm | high |
| xmdb | xmdb | false | raw-aux | dsat | dextral2 | 2006-11-29T20:10 | 2026-03-09T23:00 | 976 |  | mm? | low |
| xmdv | xmdv | false | raw-aux | dsat | voltage | 2006-11-29T20:10 | 2026-03-09T23:00 | 1270 | 12.7 | V | high |

## xmm — Middle Mtn (Parkfield)

_2 channels (2 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xmm1 | xmm1 | true | CREEP-USGS | dsat | dextral | 1984-09-24T20:30 | 2026-03-09T23:00 | 2847 | 22.16 | mm | high |
| xmmv | xmmv | false | raw-aux | dsat | voltage | 2007-05-09T00:00 | 2026-03-09T23:00 | 1270 | 12.7 | V | high |

## xmr — Melendy Ranch (SAF)

_6 channels (5 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xmr1 | xmr1 | true | CREEP-USGS | dsat | dextral | 1988-06-13T14:50 | 2019-04-13T07:00 STALE | 2042.5 | 1.97 | mm | high |
| xmr2 | xmr2 | false | CREEP-USGS | dsat | dextral | 2018-09-05T23:25 | 2026-03-09T22:51 | 15457 | 3.898 | mm | high |
| xmro | xmro | false | CREEP | dsat | orthogonal | 2020-10-21T18:30 | 2026-03-09T22:51 | 23140 | 5.408 | mm | high |
| xmrt | xmrt | false | CREEP | dsat | temp | 2020-10-21T18:30 | 2026-03-09T22:51 | -5461 | -54.61 | degC | low |
| xmrv | xmrv | false | raw-aux | dsat | voltage | 2008-05-28T23:00 | 2026-03-09T23:00 | 1247 | 12.47 | V | high |
| xmrc | xmrc | false | CREEP | dsat | CO2 | 2020-10-21T18:30 | 2026-03-09T22:51 | -89 | -89 | V(raw) | low |

## xpk — Parkfield

_2 channels (0 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xpk1 | xpk2 | true | CREEP-USGS | dsat | dextral | 1985-08-23T16:30 | 2023-03-08T23:40 STALE | 338.5 | 2.505 | mm | high |
| xpkv | xpkv | false | raw-aux | dsat | voltage | 2006-11-28T14:00 | 2023-03-08T23:40 STALE | 1317 | 13.17 | V | high |

## xrsw — Roberson, SW trace (San Andreas)

_1 channels (0 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xrsw | xrsw | true | CREEP-USGS | dsat | dextral | 2005-01-01T00:00 | 2005-12-12T22:30 STALE | 2 | 0.001867 | mm | high |

## xsc — Slack Canyon (Parkfield)

_2 channels (0 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xsc1 | xsc1 | true | CREEP-USGS | dsat | dextral | 1985-04-10T03:39 | 2022-11-15T00:39 STALE | 4651 | 37.41 | mm | high |
| xscv | xscv | false | raw-aux | dsat | voltage | 2007-01-26T18:30 | 2022-11-15T00:40 STALE | 1247 | 12.47 | V | high |

## xsh — Shore Rd (San Juan/Calaveras)

_8 channels (5 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xshh | xshh | false | CREEP | HOBO | dextral | 2020-10-14T12:00 | 2026-03-09T17:14 | 5.8204 | 5.82 | mm | high |
| xshl | xshl | false | CREEP | HOBO | dextral | 2020-10-14T12:00 | 2026-03-09T17:14 | 87.599 | 87.6 | mm | high |
| xsht | xsht | false | CREEP | HOBO | temp | 2020-10-14T12:00 | 2026-03-09T17:14 | 11.443 | 11.44 | degC | high |
| xshdp | xshdp | false | raw-aux | HOBO | dewpoint | 2020-10-14T12:00 | 2023-04-05T01:07 STALE | 13.466 | 13.47 | degC | medium |
| xshv | xshv | false | raw-aux | HOBO | voltage | 2020-10-14T12:04 | 2026-03-09T17:14 | 4.1836 | 4.184 | V | high |
| xshco | xshco | false | CREEP | HOBO | CO2 | 2020-10-14T12:00 | 2023-03-12T13:50 STALE | 2.3175 | 2.318 | V(raw) | low |
| xshrh | xshrh | false | CREEP | HOBO | rel-humidity | 2020-10-14T12:00 | 2023-04-05T01:07 STALE | 100 | 100 | %RH | high |
| xshr | xshr | false | raw-aux | HOBO | rain | 2024-03-24T02:41 | 2026-03-09T17:14 | 4.9902 | 4.99 | mm/tips? | low |

## xta — Taylor Ranch (Parkfield)

_2 channels (2 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xta1 | xta1 | true | CREEP-USGS | dsat | dextral | 1985-12-15T22:30 | 2025-07-26T05:10 | 1344 | 10.67 | mm | high |
| xtav | xtav | false | raw-aux | dsat | voltage | 2006-12-01T00:00 | 2025-07-26T05:10 | 1200 | 12 | V | high |

## xva — Varian (Parkfield)

_3 channels (0 live)_

| raw | processed | avail | pipeline | src | component | data_start | last_data | raw_val | physical | units | conf |
|-----|-----------|-------|----------|-----|-----------|------------|-----------|---------|----------|-------|------|
| xva1 | xva1 | true | CREEP-USGS | dsat | dextral | 2006-11-28T23:10 | 2021-05-31T22:50 STALE | 0 | -58.65 | mm | high |
| xvab | xvab | false | raw-aux | dsat | dextral2 | 1987-05-26T21:38 | 2021-05-31T22:58 STALE | 2583 |  | mm? | low |
| xvav | xvav | false | raw-aux | dsat | voltage | 2006-11-28T23:10 | 2021-05-31T22:50 STALE | 1270 | 12.7 | V | high |

