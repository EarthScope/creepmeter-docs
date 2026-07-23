# Creepmeter channel calibration history

_Generated 2026-07-14 from the per-station `<dir>/*.chan` files under `home/strain/MONITOR/`._

Machine-readable version: [`creepmeter_channels.csv`](creepmeter_channels.csv). See also the name/location map in [`README_CreepmeterChannels.txt`](README_CreepmeterChannels.txt).

**Notes on the `scale` column**

- Values are column 6 of the `.chan` file, verbatim.
- CREEP pipeline: scale is applied directly (`angle=0`).
- Rupture pipeline: effective gain = `scale / cos(30°)` — `monitorR+` applies the `1/cos(angle)` factor at run time from each `.id` file's `angle 30` line; it is **not** baked into the number below.
- Timestamps are ISO 8601; `open` = open-ended (`99j0000000` sentinel).

## CREEP pipeline (`home/strain/MONITOR/CREEP/`)

| dir | location | fault | component | sensor | src | start | end | scale | notes |
|-----|----------|-------|-----------|--------|-----|-------|-----|-------|-------|
| cfd_dir | Fremont Winery | Hayward | dextral (inclinometer monuments) | cfwhi | HOBO | 2021-12-19T22:00 | 2025-02-26T17:24 | -5.94255 | 5.146i 4mm/V cos(30) |
| cfd_dir | Fremont Winery | Hayward | dextral (inclinometer monuments) | cfwhi | HOBO | 2025-02-26T17:25 | open | 1.000 | switch to licor |
| cfo_dir | Fremont Winery | Hayward | orthogonal | cfwho | HOBO | 2021-12-19T22:00 | 2024-03-20T00:00 | -0.47487 | 0.47487 mm/V |
| cfo_dir | Fremont Winery | Hayward | orthogonal | cfwho | HOBO | 2024-03-20T00:01 | 2024-09-01T17:59 | -10.322 |  |
| cfo_dir | Fremont Winery | Hayward | orthogonal | cfwho | HOBO | 2024-09-01T18:00 | 2025-02-26T17:24 | 2.295 |  |
| cfo_dir | Fremont Winery | Hayward | orthogonal | cfwho | HOBO | 2025-02-26T17:25 | open | 1.000 | switch to licor |
| cfw_dir | Fremont Winery | Hayward | dextral | cfw1 | dsat | 2007-10-19T22:10 | 2020-01-07T19:31 | -0.01170 |  |
| cfw_dir | Fremont Winery | Hayward | dextral | cfw1 | dsat | 2020-01-07T19:32 | open | -0.001170 |  |
| cfw_dir | Fremont Winery | Hayward | dextral / temp-companion | cfwt | dsat | 2007-10-19T22:10 | 2020-01-07T19:25 | -0.01170 |  |
| cfw_dir | Fremont Winery | Hayward | dextral / temp-companion | cfwt | dsat | 2020-01-07T19:26 | open | -0.001170 |  |
| chp_dir | Hayward Palisades | Hayward | dextral | chp1 | dsat | 2007-10-19T22:10 | 2020-01-07T22:20 | -0.01177 |  |
| chp_dir | Hayward Palisades | Hayward | dextral | chp1 | dsat | 2020-01-07T22:25 | open | -0.001177 |  |
| chp_dir | Hayward Palisades | Hayward | dextral / temp-companion | chpt | dsat | 2007-10-19T22:10 | 2020-01-07T22:20 | -0.01177 |  |
| chp_dir | Hayward Palisades | Hayward | dextral / temp-companion | chpt | dsat | 2020-01-07T22:25 | open | -0.001177 |  |
| coz_dir | Oakland Zoo | Hayward | dextral | coz1 | dsat | 2007-10-19T22:10 | 2019-12-09T15:30 | -0.0117 |  |
| coz_dir | Oakland Zoo | Hayward | dextral | coz3 | dsat | 2019-12-09T15:35 | 2019-12-24T00:55 | -0.002506 | 2.17mm/Volt range is 0.210 to 4.820 volts 10 mm range (30 degrees) |
| coz_dir | Oakland Zoo | Hayward | dextral | coz1 | dsat | 2019-12-24T01:00 | 2020-01-07T17:29 | -0.02346 | lvdt -20.524mm/Volt; 0 to 4 inches |
| coz_dir | Oakland Zoo | Hayward | dextral | coz1 | dsat | 2020-01-07T17:30 | 2024-11-04T03:00 | -0.002346 | increased resolution by 10X |
| coz_dir | Oakland Zoo | Hayward | dextral | coz3 | dsat | 2024-11-04T03:01 | 2025-03-05T19:08 | 0.000281 | rescaled to match lvdt rate; 0.000217 2.17mm/Volt range is 0.210 to 4.820 volts 10X |
| coz_dir | Oakland Zoo | Hayward | dextral | coz1 | dsat | 2025-03-05T19:09 | open | -0.0011675 | replaced lvdt with 2-inch range |
| coz_dir | Oakland Zoo | Hayward | dextral / temp-companion | cozt | dsat | 2007-10-19T22:10 | 2020-01-07T17:29 | -0.0117 |  |
| coz_dir | Oakland Zoo | Hayward | dextral / temp-companion | cozt | dsat | 2020-01-07T17:30 | open | -0.00117 | increased resolution by 10X |
| cpp_dir | Pt Pinole | Hayward | dextral | cpp1 | dsat | 1995-08-16T21:40 | 2020-01-22T19:45 | -0.01174 |  |
| cpp_dir | Pt Pinole | Hayward | dextral | cpp1 | dsat | 2020-01-22T19:46 | 2020-07-07T15:29 | -0.001174 |  |
| cpp_dir | Pt Pinole | Hayward | dextral | cpp1 | dsat | 2020-07-07T15:30 | 2024-06-28T00:00 | -0.001180 |  |
| cpp_dir | Pt Pinole | Hayward | dextral | cpp3 | dsat | 2024-06-28T00:01 | open | 0.000292 | rescaled by 15% to match lvdt rate; 0.0002513 using hall sensor |
| cpp_dir | Pt Pinole | Hayward | dextral / temp-companion | cppt | dsat | 1995-08-16T21:40 | 2020-01-22T19:45 | -0.01174 |  |
| cpp_dir | Pt Pinole | Hayward | dextral / temp-companion | cppt | dsat | 2020-01-22T19:46 | 2020-07-07T15:29 | -0.001174 |  |
| cpp_dir | Pt Pinole | Hayward | dextral / temp-companion | cppt | dsat | 2020-07-07T15:30 | open | -0.001180 |  |
| ctm_dir | Temescal | Hayward | dextral | ctm1 | dsat | 2007-10-19T22:10 | 2020-01-07T16:20 | -0.0118 |  |
| ctm_dir | Temescal | Hayward | dextral | ctm1 | dsat | 2020-01-07T16:25 | 2020-06-09T21:59 | -0.00118 |  |
| ctm_dir | Temescal | Hayward | dextral | ctm1 | dsat | 2020-06-09T22:00 | 2024-07-16T17:49 | -0.001173 |  |
| ctm_dir | Temescal | Hayward | dextral | ctm1 | dsat | 2024-07-16T17:50 | open | -0.001148 | Calib sheet says 2.5263 v/in or 0.0995 V/mm -- 30 deg oblib yiels 0.001148 |
| ctm_dir | Temescal | Hayward | dextral / temp-companion | ctmt | dsat | 2007-10-19T22:10 | 2020-01-07T16:20 | -0.0118 |  |
| ctm_dir | Temescal | Hayward | dextral / temp-companion | ctmt | dsat | 2020-01-07T16:25 | 2020-06-09T21:59 | -0.00118 |  |
| ctm_dir | Temescal | Hayward | dextral / temp-companion | ctmt | dsat | 2020-06-09T22:00 | open | -0.001173 |  |
| cwc_dir | Cienega Winery | San Juan SAF | CO2 | cwn4 | dsat | 2020-09-03T23:00 | open | 0.0001 | output in volts; 1000ppm/v |
| cwc_dir | Cienega Winery | San Juan SAF | CO2 / temp-companion | cwn3 | dsat | 2020-09-03T23:00 | open | 0.0002190 | 2.190 mm/volt |
| cwo_dir | Cienega Winery | San Juan SAF | orthogonal | cwn3 | dsat | 2020-09-03T23:00 | open | 0.0002190 | 2.190 mm/volt |
| cwo_dir | Cienega Winery | San Juan SAF | orthogonal / temp-companion | cwn3 | dsat | 2020-09-03T23:00 | open | 0.0002190 | 2.190 mm/volt |
| cwp_dir | Cienega Winery | San Juan SAF | dextral | cwn2 | dsat | 2020-09-03T23:00 | open | 0.0002193 | 2.193 mm/volt |
| cwp_dir | Cienega Winery | San Juan SAF | dextral / temp-companion | cwn2 | dsat | 2020-09-03T23:00 | open | 0.0002193 | 2.193 mm/volt |
| frd_dir | Fox Ranch-south | San Juan SAF | dextral | xfrd | HOBO | 2022-06-03T00:00 | 2025-02-26T17:54 | 2.791 | 2.791 mm/V |
| frd_dir | Fox Ranch-south | San Juan SAF | dextral | xfrd | HOBO | 2025-02-26T17:55 | open | 1.000 | switch to licor |
| fro_dir | Fox Ranch-south | San Juan SAF | orthogonal | xfro | HOBO | 2022-06-03T00:00 | 2025-02-26T17:54 | 2.334 | 2.334 mm/V |
| fro_dir | Fox Ranch-south | San Juan SAF | orthogonal | xfro | HOBO | 2025-02-26T17:55 | open | 1.000 | switch to licor |
| fwo_dir | Fremont Winery | Hayward | orthogonal (alt of cfo) | cfwho | HOBO | 2021-12-09T19:00 | open | -0.47487 | mm/V |
| fwo_dir | Fremont Winery | Hayward | orthogonal (alt of cfo) / temp-companion | cfwt | dsat | 2007-10-19T22:10 | 2020-01-07T19:25 | -0.01170 |  |
| fwo_dir | Fremont Winery | Hayward | orthogonal (alt of cfo) / temp-companion | cfwt | dsat | 2020-01-07T19:26 | open | -0.001170 |  |
| mee_dir | Mee Ranch | SAF | dextral | meed | HOBO | 2021-03-31T00:00 | 2024-01-01T00:00 | 2.791 | 2.791 mm/V |
| mee_dir | Mee Ranch | SAF | dextral | meed | HOBO | 2024-01-01T00:01 | 2025-02-26T17:54 | 2.373 |  |
| mee_dir | Mee Ranch | SAF | dextral | meed | HOBO | 2025-02-26T17:55 | open | 1.000 | switch to licor |
| meo_dir | Mee Ranch | SAF | orthogonal | meeo | HOBO | 2021-03-31T00:00 | 2024-01-01T00:00 | 2.334 | 2.334 mm/V |
| meo_dir | Mee Ranch | SAF | orthogonal | meeo | HOBO | 2024-01-01T00:01 | 2025-02-26T17:54 | 2.350 |  |
| meo_dir | Mee Ranch | SAF | orthogonal | meeo | HOBO | 2025-02-26T17:55 | open | 1.000 | switch to licor |
| met_dir | Mee Ranch | SAF | temperature | meet | HOBO | 2021-03-31T00:00 | 2024-01-01T00:00 | 1.0 | deg-C |
| met_dir | Mee Ranch | SAF | temperature | meet | HOBO | 2024-01-01T00:01 | open | 0.1 | deg-C |
| mrc_dir | Melendy Ranch | SAF | CO2 | xmrc | dsat | 2020-10-21T18:00 | open | 0.0001 | output in volts; 1000ppm/v |
| mrc_dir | Melendy Ranch | SAF | CO2 / temp-companion | xmrc | dsat | 2020-10-21T18:00 | open | 0.0001 | output in volts; 1000ppm/v |
| mro_dir | Melendy Ranch | SAF | orthogonal | xmro | dsat | 2020-10-21T18:00 | open | 0.0002337 | 2.337 mm/V 10mm wrap |
| mro_dir | Melendy Ranch | SAF | orthogonal / temp-companion | xmro | dsat | 2020-10-21T18:00 | open | 0.0002337 | 2.337 mm/V 10mm wrap |
| mrt_dir | Melendy Ranch | SAF | temperature | xmrt | dsat | 2020-10-21T18:00 | open | 0.001 | 10C/volt |
| mrt_dir | Melendy Ranch | SAF | temperature / temp-companion | xmrt | dsat | 2020-10-21T18:00 | open | 0.001 | 10C/volt |
| nfd_dir | Fox Ranch-north | San Juan SAF | dextral | xfrnd | HOBO | 2025-08-01T00:00 | 2025-09-08T14:35 | 2.657 | mm/V |
| nfd_dir | Fox Ranch-north | San Juan SAF | dextral | xfrnd | HOBO | 2025-09-08T14:36 | open | 1.000 | switch to licor |
| nfo_dir | Fox Ranch-north | San Juan SAF | orthogonal | xfrno | HOBO | 2025-08-01T00:00 | 2025-09-08T14:35 | 2.278 | mm/V |
| nfo_dir | Fox Ranch-north | San Juan SAF | orthogonal | xfrno | HOBO | 2025-09-08T14:36 | open | 1.000 | switch to licor |
| nfo_dir | Fox Ranch-north | San Juan SAF | orthogonal | xfrno | HOBO | 2025-08-01T00:00 | 2025-09-08T14:35 | 2.278 | mm/V |
| nfo_dir | Fox Ranch-north | San Juan SAF | orthogonal | xfrno | HOBO | 2025-09-08T14:36 | open | 1.000 | switch to licor |
| sfr_dir | St Francis | San Juan SAF | dextral | sfrd | HOBO | 2021-03-31T00:00 | 2024-01-01T00:00 | 2.3315 | mm/V |
| sfr_dir | St Francis | San Juan SAF | dextral | sfrd | HOBO | 2024-01-01T00:01 | 2025-02-26T17:54 | 2.15 |  |
| sfr_dir | St Francis | San Juan SAF | dextral | sfrd | HOBO | 2025-02-26T17:55 | 2025-10-30T21:57 | 1.000 | switch to licor |
| sfr_dir | St Francis | San Juan SAF | dextral | sf2d | HOBO | 2025-10-30T21:58 | open | 1.000 | use sf2d ssite2025 303.914583 |
| shc_dir | Shore Rd | San Juan/Calaveras | CO2 | xshco | HOBO | 2020-10-21T18:00 | open | 1000. | output in volts; 1000ppm/v |
| shl_dir | Shore Rd | San Juan/Calaveras | dextral (low-res) | xshl | HOBO | 2020-09-26T00:00 | 2025-02-26T17:43 | 34.3 | 34.3 mm/V |
| shl_dir | Shore Rd | San Juan/Calaveras | dextral (low-res) | xshl | HOBO | 2025-02-26T17:44 | open | 1.0 | licor |
| shl_dir | Shore Rd | San Juan/Calaveras | dextral (low-res) | xshl | HOBO | 2020-09-26T00:00 | 2025-02-26T17:43 | 34.3 | 34.3 mm/V |
| shl_dir | Shore Rd | San Juan/Calaveras | dextral (low-res) | xshl | HOBO | 2025-02-26T17:44 | open | 1.0 | switch to licor |
| shr_dir | Shore Rd | San Juan/Calaveras | relative humidity | xshrh | HOBO | 2020-10-21T18:00 | open | 1. | output in relative humidity |
| sht_dir | Shore Rd | San Juan/Calaveras | temperature | xsht | HOBO | 2020-10-21T18:00 | open | 1. | output in deg C |
| sjb_dir | San Juan | San Juan SAF | dextral | xsjd | HOBO | 2024-01-01T00:01 | 2025-02-26T17:54 | 2.1938 |  |
| sjb_dir | San Juan | San Juan SAF | dextral | xsjd | HOBO | 2025-02-26T17:55 | open | 1.000 | switch to licor |
| sjn_dir | San Juan Nyland | San Juan SAF | dextral | sjnh | HOBO | 2020-09-26T00:00 | 2025-02-26T17:54 | 2.668 | 2.668 mm/V scale |
| sjn_dir | San Juan Nyland | San Juan SAF | dextral | sjnh | HOBO | 2025-02-26T17:55 | open | 1.000 | switch to licor |
| xsh_dir | Shore Rd | San Juan/Calaveras | dextral | xshh | HOBO | 2020-09-26T00:00 | 2024-01-01T00:00 | 2.985 | 3.8975 # 2.985 mm/V scale 1/cos(40) |
| xsh_dir | Shore Rd | San Juan/Calaveras | dextral | xshh | HOBO | 2024-01-01T00:01 | 2025-02-26T17:54 | 3.743 |  |
| xsh_dir | Shore Rd | San Juan/Calaveras | dextral | xshh | HOBO | 2025-02-26T17:55 | open | 1.000 | switch to licor |

## Rupture pipeline (`home/strain/MONITOR/Rupture/`)

| dir | location | res | sensor | src | start | end | scale (pre-cos) | notes |
|-----|----------|-----|--------|-----|-------|-----|-----------------|-------|
| cfwHR_dir | Fremont Winery | HR | cfw2 | dsat | 2014-08-27T00:00 | 2020-01-08T19:40 | -0.0254 |  |
| cfwHR_dir | Fremont Winery | HR | cfw2 | dsat | 2020-01-08T19:45 | 2020-06-26T20:35 | -0.00254 | increase resolution by 10X |
| cfwHR_dir | Fremont Winery | HR | cfw3 | dsat | 2020-06-26T20:40 | open | 0.000267 | 2.311 mm/V |
| cfwLR_dir | Fremont Winery | LR | cfw3 | dsat | 2014-08-27T00:00 | 2020-01-07T19:40 | 0.4105 |  |
| cfwLR_dir | Fremont Winery | LR | cfw3 | dsat | 2020-01-07T19:45 | 2020-06-26T20:35 | 0.04105 | increase resolution by 10X |
| cfwLR_dir | Fremont Winery | LR | cfw2 | dsat | 2020-06-26T20:40 | open | 0.02687 | 232.7mm/volt |
| chpHR_dir | Hayward Palisades | HR | chp3 | dsat | 2014-07-28T00:00 | 2020-01-02T21:55 | -0.025 |  |
| chpHR_dir | Hayward Palisades | HR | chp2 | dsat | 2020-01-02T22:00 | 2020-01-03T16:55 | 0.002213 |  |
| chpHR_dir | Hayward Palisades | HR | chp3 | dsat | 2020-01-03T17:00 | 2020-01-07T22:05 | 0.002213 |  |
| chpHR_dir | Hayward Palisades | HR | chp3 | dsat | 2020-01-07T22:10 | open | 0.0002213 | Increase resolution by 10X |
| chpLR_dir | Hayward Palisades | LR | chp2 | dsat | 2014-07-28T00:00 | 2020-01-02T21:55 | 0.40 |  |
| chpLR_dir | Hayward Palisades | LR | chp3 | dsat | 2020-01-02T22:00 | 2020-01-03T16:55 | 0.23737 |  |
| chpLR_dir | Hayward Palisades | LR | chp2 | dsat | 2020-01-03T17:00 | 2020-01-07T22:05 | 0.23737 |  |
| chpLR_dir | Hayward Palisades | LR | chp2 | dsat | 2020-01-07T22:10 | open | 0.023737 | increase resolution by 10X |
| cozHR_dir | Oakland Zoo | HR | coz3 | dsat | 2014-07-27T00:00 | 2019-11-17T21:55 | -0.025 |  |
| cozHR_dir | Oakland Zoo | HR | coz3 | dsat | 2019-11-17T22:00 | 2020-01-07T17:35 | +0.00217 | 2.17mm/Volt range is 0.210 to 4.820 volts |
| cozHR_dir | Oakland Zoo | HR | coz3 | dsat | 2020-01-07T17:36 | open | +0.000217 | 2.17mm/Volt range is 0.210 to 4.820 volts 10X |
| cozLR_dir | Oakland Zoo | LR | coz2 | dsat | 2014-07-27T00:00 | 2019-11-17T21:55 | 0.40 |  |
| cozLR_dir | Oakland Zoo | LR | coz2 | dsat | 2019-11-17T22:00 | 2020-01-07T17:35 | 0.23783 | 237.83 mm/V range is 0.0476 to 4.946 |
| cozLR_dir | Oakland Zoo | LR | coz2 | dsat | 2020-01-07T17:37 | open | 0.023783 | 237.83 mm/V range is 0.0476 to 4.946 10X |
| cppHR_dir | Pt Pinole | HR | cpp3 | dsat | 2014-07-24T00:00 | 2019-12-09T00:25 | -0.025 |  |
| cppHR_dir | Pt Pinole | HR | cpp2 | dsat | 2019-12-09T00:30 | 2019-12-26T22:05 | 0.002513 | 0.002538 # 2.1767 mm/volt range 10 mm between 0.2047 and 4.7987 volts Unknown sig |
| cppHR_dir | Pt Pinole | HR | cpp3 | dsat | 2019-12-26T22:10 | 2020-01-22T18:45 | 0.002513 | 0.002538 # 2.1767 mm/volt range 10 mm between 0.2047 and 4.7987 volts Unknown sign |
| cppHR_dir | Pt Pinole | HR | cpp3 | dsat | 2020-01-22T18:50 | open | 0.0002513 | 0.0002538 # 2.1767 mm/volt range 10 mm between 0.2047 and 4.7987 volts Unknown sign |
| cppLR_dir | Pt Pinole | LR | cpp2 | dsat | 2014-07-24T00:00 | 2018-09-10T23:50 | 0.40 |  |
| cppLR_dir | Pt Pinole | LR | cpp2 | dsat | 2018-09-11T00:00 | 2019-11-14T21:55 | 0.2382 | note (238.2mm/V; range from 0.00 to 4.89 volts |
| cppLR_dir | Pt Pinole | LR | cpp2 | dsat | 2019-11-14T22:00 | 2019-12-09T00:25 | 0.23783 | 237.83 mm/V |
| cppLR_dir | Pt Pinole | LR | cpp3 | dsat | 2019-12-09T00:30 | 2019-12-26T22:05 | 0.2396 | 0.049 to 4.948 range |
| cppLR_dir | Pt Pinole | LR | cpp2 | dsat | 2019-12-26T22:10 | 2020-01-22T18:45 | 0.2396 | 0.049 to 4.948 range |
| cppLR_dir | Pt Pinole | LR | cpp2 | dsat | 2020-01-22T18:50 | open | 0.02396 | 0.049 to 4.948 range |
| ctmHR_dir | Temescal | HR | ctm3 | dsat | 2012-11-01T00:00 | 2014-12-06T17:50 | +0.075 |  |
| ctmHR_dir | Temescal | HR | ctm3 | dsat | 2014-12-06T18:00 | 2020-01-07T14:50 | 0.0254 | not sure off SIGN for sense of slip |
| ctmHR_dir | Temescal | HR | ctm3 | dsat | 2020-01-07T14:55 | 2020-06-09T21:59 | 0.00254 | increase resolution by 10X |
| ctmHR_dir | Temescal | HR | ctm3 | dsat | 2020-06-09T22:00 | open | 0.000261 | new sensor |
| ctmLR_dir | Temescal | LR | ctm2 | dsat | 2012-11-02T00:00 | 2014-12-06T17:50 | -0.60 |  |
| ctmLR_dir | Temescal | LR | ctm2 | dsat | 2014-12-06T18:00 | 2020-01-07T14:50 | 0.4105 | not sure off SIGN for sense of slip |
| ctmLR_dir | Temescal | LR | ctm2 | dsat | 2020-01-07T14:55 | 2020-06-09T21:55 | 0.04105 | increase resolution by 10X |
| ctmLR_dir | Temescal | LR | ctm2 | dsat | 2020-06-09T22:00 | open | 0.027736 | new sensor |

