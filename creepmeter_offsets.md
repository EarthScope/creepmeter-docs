# Creepmeter channel replacement & offset history

_Parsed 2026-07-20 from `metadata/HDR/*.hdr1` narrative headers._ Machine-readable: [`creepmeter_offsets.csv`](creepmeter_offsets.csv), [`creepmeter_lineage.csv`](creepmeter_lineage.csv).

These explain the sensor swaps in [`creepmeter_channels.csv`](creepmeter_channels.csv): each `.chan` sensor change (cpp1→cpp3, coz1→coz3, sfrd→sf2d, `switch to licor`) traces to an event below.

**Offset codes:** `N` = offset/step, `S N` = paired/secondary reset (~1 day apart, dead-pot artifact), `T` = rain-response tag, `M` = manual offset with lost baseline.

## Channel-ID replacement lineage

| site | predecessor | → | successor | approx date | reason |
|------|-------------|---|-----------|-------------|--------|
| Harris Ranch | xhr1 | → | xhr2 | 2004-06 | xhr2 conduit caved-in; xhr1 was 1981-86 reconstruction |
| Harris Ranch | xhr2 | → | xhr3 | 2009-08 | conduit repaired, re-established as xhr3 |
| San Juan Bautista | xsj2 | → | xsj3 | 2007-02 | new invar wire = NEW ZERO |
| Parkfield | xpk1 | → | xpk2 | 2004-09-28 | wire broke in Parkfield EQ, zero lost |
| Melendy Ranch | xmr1 | → | xmr2 | 2018-09-05 | rebuilt after 2014 break; ~4yr gap, zero lost |
| Highway 46 | x461 | → | c461 | 2016-12-11 | x461 wire broke (unremediable); c461 = Bilham post-2004 install |
| Shore Rd | xsh(1971/85) | → | xshr1(2020) | 2020 | destroyed 2017; new Hall-effect rotary 2020 |
| San Juan Nyland | sjn(2004) | → | sjn(2020) | 2020 | Bilham reinstall (flood-resistant); Nason orig 1967 |
| Cienega Winery | cwc3 | → | cwn1 | 2000 | cwc3 unreliable (bolts stripped); cwn1 primary |
| St Francis | sfrd | → | sf2d | 2025-10-30 | processing switched to St Francis #2 (~100 m N) |

## Offset events per sensor (by category)

| sensor | events | span | sensor-swap | wire-reset | electronics | rain | damage | site-visit | offset | other | unspecified |
|--------|-------|------|-|-|-|-|-|-|-|-|-|
| c461 | 6 | 2011-07..2026-03 | 1 | 2 |  |  | 1 | 1 | 1 |  |  |
| cfw1 | 8 | 2010-11..2024-01 | 1 | 4 |  |  |  | 3 |  |  |  |
| chp1 | 9 | 2009-08..2023-01 | 1 |  |  |  |  | 5 | 3 |  |  |
| coz1 | 10 | 2014-07..2025-04 | 6 | 1 |  |  |  | 2 | 1 |  |  |
| cpp1 | 20 | 2009-10..2024-06 | 9 | 1 | 6 |  |  | 2 | 2 |  |  |
| crr1 | 5 | 2014-02..2015-06 |  | 5 |  |  |  |  |  |  |  |
| ctm1 | 6 | 2009-05..2025-04 | 4 | 1 |  |  |  | 1 |  |  |  |
| cwc3 | 13 | 2014-01..2022-03 | 3 | 5 |  |  | 1 | 4 |  |  |  |
| cwn1 | 13 | 2014-01..2022-03 | 3 | 5 |  |  | 1 | 4 |  |  |  |
| sjn1 | 3 | 2022-05..2025-02 |  | 1 | 1 |  |  | 1 |  |  |  |
| wkr1 | 68 | 2014-03..2025-06 | 2 | 66 |  |  |  |  |  |  |  |
| x461 | 3 | 2014-02..2015-04 |  | 1 | 1 |  | 1 |  |  |  |  |
| xgh1 | 10 | 2014-05..2019-04 | 1 | 8 |  |  | 1 |  |  |  |  |
| xhr3 | 6 | 2014-04..2022-08 |  | 6 |  |  |  |  |  |  |  |
| xmd1 | 12 | 2014-04..2026-03 |  | 10 |  | 1 |  |  | 1 |  |  |
| xmm1 | 11 | 2014-03..2026-03 |  | 9 |  |  |  |  | 2 |  |  |
| xmr1 | 24 | 2014-01..2024-12 |  | 15 | 3 |  |  | 5 | 1 |  |  |
| xpk1 | 5 | 2014-01..2019-04 |  | 5 |  |  |  |  |  |  |  |
| xpk2 | 5 | 2014-01..2019-04 |  | 5 |  |  |  |  |  |  |  |
| xsc1 | 12 | 2014-01..2021-06 |  | 9 |  | 3 |  |  |  |  |  |
| xsh1 | 6 | 2020-10..2025-02 |  | 4 | 1 |  |  |  |  |  | 1 |
| xsj3 | 5 | 2014-04..2015-06 |  | 1 |  |  |  | 4 |  |  |  |
| xta1 | 8 | 2014-01..2024-11 |  | 8 |  |  |  |  |  |  |  |
| xva1 | 2 | 2014-01..2015-05 |  | 2 |  |  |  |  |  |  |  |

_Total 270 offset events across 24 sensors._
