# Creepmeter merge QC (Patch_merge.dat)

_Parsed 2026-07-23 from every `home/strain/MONITOR/CREEP/*_dir/Patch_merge.dat`_ — the diagnostic log `Merge1.3+` writes each time it stitches a new cleanstrain chunk onto the running merged series. Machine-readable: [`creepmeter_merge_qc.csv`](creepmeter_merge_qc.csv). See [`creepmeter_merge_mapping.md`](creepmeter_merge_mapping.md) for which channel feeds each site's merge.

**Columns**: `diff_mm` = LSQ-estimated offset applied to align this chunk with the running merged series (cumulative — large jumps correspond to real resets, cross-check against [`creepmeter_offsets.csv`](creepmeter_offsets.csv)). `rms` = misfit of that alignment (mm). `n_overlap` = overlapping timestamped samples supporting the estimate. `diff_jump_mm` = change from the previous segment's diff for that channel.

**`quality` flags** (in priority order): `gap_no_overlap` (n=0, no basis for the offset estimate) · `high_rms` (≥1.0 mm, poor fit) · `elevated_rms` (0.1–1.0 mm) · `low_overlap` (<5000 samples, less robust) · `large_offset_jump` (≥5mm step from previous segment — usually a real wire-reset/sensor-swap, not an error) · `ok`.

**804 total merge events** across 44 sites: ok=634 · large_offset_jump=107 · elevated_rms=31 · gap_no_overlap=15 · high_rms=10 · low_overlap=7

## Flagged segments (everything except plain `ok` / `large_offset_jump`)

These are the rows worth a human look — poor fits or missing overlap, not just routine resets.

| site | channel | segment | diff_mm | rms | n_overlap | quality |
|------|---------|---------|---------|-----|-----------|---------|
| mee | meed | A25188 | -35.985 | 2.4 | 45645 | high_rms |
| mee | meed | A25251 | -35.984 | 2.06 | 61756 | high_rms |
| met | meet | A24254 | -1.349 | 4.44 | 18367 | high_rms |
| met | meet | A25038 | -2.243 | 3.61 | 24043 | high_rms |
| met | meet | A25188 | -2.242 | 2.62 | 45643 | high_rms |
| met | meet | A25251 | -2.241 | 2.25 | 61767 | high_rms |
| nfd | xfrnd | MON | 9.717 | 1.96 | 231382 | high_rms |
| sfr | sfrd | MON | -14.633 | 3.79 | 12979 | high_rms |
| shc | xshco | A23050 | -0.002 | 2.44 | 79283 | high_rms |
| shc | xshco | A23216 | -0.003 | 2.47 | 77666 | high_rms |
| c46 | c461 | A12260 | -0.113 | 0.46 | 27165 | elevated_rms |
| c46 | c461 | A12346 | -0.11 | 0.25 | 90044 | elevated_rms |
| cfw | cfw1 | A10301 | -145.325 | 0.31 | 38963 | elevated_rms |
| cfw | cfw1 | A11022 | -145.279 | 0.14 | 82533 | elevated_rms |
| cfw | cfw1 | A11108 | -145.264 | 0.11 | 82306 | elevated_rms |
| cfw | cfw1 | A11194 | -145.273 | 0.1 | 83463 | elevated_rms |
| chp | chp1 | A16114 | -129.596 | 0.1 | 78935 | elevated_rms |
| cpp | cpp1 | A20167 | -101.226 | 0.17 | 58192 | elevated_rms |
| cpp | cpp1 | A25153 | -136.523 | 0.14 | 71482 | elevated_rms |
| cpp | cpp1 | A25251 | -136.507 | 0.12 | 79052 | elevated_rms |
| cpp | cpp1 | A26035 | -136.535 | 0.26 | 73079 | elevated_rms |
| crr | crr1 | A14328 | -278.27 | 0.13 | 62736 | elevated_rms |
| crr | crr1 | A15195 | -278.03 | 0.16 | 81600 | elevated_rms |
| crr | crr1 | A16269 | -275.47 | 0.32 | 81409 | elevated_rms |
| crr | crr1 | A17049 | -275.09 | 0.2 | 81551 | elevated_rms |
| ctm | ctm1 | A20355 | -134.304 | 0.28 | 23371 | elevated_rms |
| nfo | xfrno | A26035 | 8.278 | 0.11 | 232007 | elevated_rms |
| nfo | xfrno | MON | 8.223 | 0.28 | 231389 | elevated_rms |
| wkr | wkr1 | MON | -489.836 | 0.14 | 18279 | elevated_rms |
| xta | xta1 | A16115 | -473.463 | 0.11 | 80894 | elevated_rms |
| xva | xva1 | A14156 | -466.15 | 0.12 | 37999 | elevated_rms |
| xva | xva1 | A14242 | -465.92 | 0.15 | 50352 | elevated_rms |
| xva | xva1 | A14328 | -465.74 | 0.31 | 62736 | elevated_rms |
| xva | xva1 | A15049 | -465.85 | 0.18 | 75120 | elevated_rms |
| xva | xva1 | A15195 | -465.8 | 0.2 | 81600 | elevated_rms |
| xva | xva1 | A15341 | -465.8 | 0.17 | 81599 | elevated_rms |
| xva | xva1 | A16122 | -485.19 | 0.56 | 81636 | elevated_rms |
| xva | xva1 | A16224 | -484.96 | 0.33 | 87901 | elevated_rms |
| xva | xva1 | A16269 | -484.13 | 0.71 | 96109 | elevated_rms |
| xva | xva1 | A17049 | -484.91 | 0.34 | 81561 | elevated_rms |
| xva | xva1 | A17195 | -494.85 | 0.35 | 81620 | elevated_rms |
| cfd | cfwhi | A26056 | 0.0 |  | 0 | gap_no_overlap |
| mee | meed | MON | 0.0 |  | 0 | gap_no_overlap |
| meo | meeo | MON | 0.0 |  | 0 | gap_no_overlap |
| met | meet | MON | 0.0 |  | 0 | gap_no_overlap |
| nfd | xfrnd | A25251 | 0.0 |  | 0 | gap_no_overlap |
| nfd | xfrnd | A26035 | 0.0 |  | 0 | gap_no_overlap |
| nfo | xfrno | A25251 | 0.0 |  | 0 | gap_no_overlap |
| shc | xshco | MON | 0.0 |  | 0 | gap_no_overlap |
| shr | xshrh | MON | 0.0 |  | 0 | gap_no_overlap |
| sjn | sjnh | MON | 0.0 |  | 0 | gap_no_overlap |
| xgh | xgh1 | MON | 0.0 |  | 0 | gap_no_overlap |
| xmd | xmd1 | A24325 | -593.93 | 0.0 | 2880 | low_overlap |
| xmd | xmd1 | A25109 | -593.93 | 0.0 | 2018 | low_overlap |
| xmm | xmm1 | A21242 | -778.77 | 0.0 | 4433 | low_overlap |
| xmm | xmm1 | A25109 | -778.77 | 0.0 | 1745 | low_overlap |
| xmr2014 | xmr1 | A19110 |  |  | 0 | gap_no_overlap |
| xmr2014 | xmr1 | MON |  |  | 0 | gap_no_overlap |
| xpk | xpk2 | MON | -276.242 | 0.0 | 2065 | low_overlap |
| xsc | xsc1 | A21199 | -720.611 | 0.0 | 4753 | low_overlap |
| xsc | xsc1 | MON | 0.0 |  | 0 | gap_no_overlap |
| xta | xta1 | A14058 | -463.1 | 0.0 | 3025 | low_overlap |
| xta | xta1 | MON | 0.0 |  | 0 | gap_no_overlap |

## Large offset jumps (≥5mm step — cross-check against known resets)

| site | channel | segment | diff_mm | diff_jump_mm | n_overlap |
|------|---------|---------|---------|--------------|-----------|
| xmm | xmm1 | A14156 | -681.96 | -681.96 | 37265 |
| xsc | xsc1 | A14156 | -601.799 | -601.799 | 37980 |
| xmd | xmd1 | A14156 | -515.329 | -515.329 | 35345 |
| xta | xta1 | A14059 | -0.006 | 463.094 | 98528 |
| xta | xta1 | A14145 | -463.1 | -463.094 | 34514 |
| wkr | wkr1 | A14156 | -410.254 | -410.254 | 31252 |
| xmr2014 | xmr1 | A14156 | -377.33 | -377.33 | 38007 |
| cwn | cwn1 | A14156 | -285.89 | -285.89 | 36208 |
| crr | crr1 | A14156 | -278.16 | -278.16 | 38078 |
| xpk | xpk2 | A14158 | -206.71 | -206.71 | 37218 |
| xgh | xgh1 | A14156 | -141.509 | -141.509 | 35786 |
| coz | coz1 | A22103 | -179.08 | -82.57 | 81679 |
| xmm | xmm1 | A21200 | -778.77 | -68.78 | 17809 |
| c46 | c461 | MON | -53.57 | -66.975 | 18288 |
| cfw | cfw1 | A26038 | -255.67 | -53.78 | 80701 |
| cwn | cwn1 | MON | -433.983 | -52.621 | 15406 |
| xhr | xhr3 | A14158 | -49.87 | -49.87 | 38199 |
| xsj | xsj3 | A14158 | -49.56 | -49.56 | 38102 |
| cpp | cpp1 | MON | -89.19 | 47.345 | 18288 |
| cfd | cfwhi | MON | 46.77 | 46.77 | 21295 |
| cfw | cfw1 | A18259 | -203.95 | -44.252 | 78416 |
| ctm | ctm1 | A18259 | -133.908 | -38.05 | 78527 |
| coz | coz1 | A16260 | -96.51 | -36.362 | 81573 |
| xpk | xpk2 | A18269 | -245.692 | -29.969 | 81789 |
| cfo | cfwho | MON | 29.27 | 29.261 | 18288 |
| cwn | cwn1 | A22357 | -381.357 | -28.95 | 78770 |
| xsh | xshh | A26044 | -40.83 | -27.133 | 70497 |
| cpp | cpp1 | A16260 | -101.226 | -25.744 | 81334 |
| frd | xfrd | MON | -38.244 | -25.454 | 18197 |
| mrt | xmrt | MON | -25.0 | -25.0 | 18288 |
| chp | chp1 | A16260 | -153.995 | -24.399 | 80190 |
| mee | meed | A24104 | -24.33 | -24.322 | 35771 |
| coz | coz1 | A22249 | -155.66 | 23.42 | 81725 |
| xmr | xmr2 | MON | -727.01 | -23.13 | 18143 |
| x46 | x461 | A16179 | 19.68 | 22.46 | 60108 |
| xsc | xsc1 | A16122 | -624.185 | -22.397 | 80647 |
| xsj | xsj3 | MON | -73.02 | -22.34 | 7453 |
| xta | xta1 | A18260 | -503.561 | -21.736 | 73184 |
| cwn | cwn1 | A19033 | -334.758 | -21.638 | 47655 |
| xmr | xmr2 | A24068 | -682.804 | -21.436 | 39678 |
| xsc | xsc1 | A21242 | -741.461 | -20.85 | 35140 |
| cwp | cwn2 | MON | -30.267 | -20.07 | 30240 |
| cfw | cfw1 | A12345 | -164.035 | -18.768 | 89717 |
| cpp | cpp1 | A22104 | -129.683 | -18.691 | 77765 |
| xhr | xhr3 | A22191 | -114.853 | -18.611 | 81547 |
| xmd | xmd1 | A16122 | -533.746 | -18.416 | 81636 |
| cpp | cpp1 | A21242 | -111.349 | 18.327 | 75430 |
| cpp | cpp1 | A21104 | -129.676 | -18.319 | 44853 |
| cwn | cwn1 | A17179 | -313.123 | -18.016 | 74302 |
| cwn | cwn1 | A19325 | -352.407 | -17.649 | 80916 |
| xgh | xgh1 | A19195 | -172.042 | -16.576 | 73700 |
| xmr | xmr2 | A21241 | -650.746 | 16.223 | 96525 |
| xmm | xmm1 | A18162 | -709.99 | -15.64 | 80311 |
| xhr | xhr3 | A19033 | -88.21 | -15.46 | 81789 |
| xsc | xsc1 | A17195 | -651.97 | -15.324 | 80277 |
| xpk | xpk2 | A21195 | -276.241 | -15.273 | 78712 |
| xpk | xpk2 | A20123 | -260.949 | -15.255 | 81056 |
| xsh | xshh | A23050 | -13.697 | -13.668 | 78696 |
| xsc | xsc1 | A18268 | -673.722 | -13.468 | 74621 |
| wkr | wkr1 | A17195 | -423.639 | -13.376 | 60538 |
| wkr | wkr1 | A22045 | -459.177 | -13.17 | 78476 |
| wkr | wkr1 | A19014 | -436.949 | -13.152 | 81776 |
| xhr | xhr3 | A17179 | -72.752 | -13.031 | 78756 |
| frd | xfrd | A24258 | -12.79 | -12.79 | 54409 |
| xta | xta1 | A21200 | -516.23 | -12.668 | 42506 |
| mee | meed | A24254 | -36.99 | -12.66 | 16801 |
| xsc | xsc1 | A16269 | -636.637 | -12.452 | 80628 |
| sjn | sjnh | A25017 | -9.04 | -12.26 | 13902 |
| coz | coz1 | MON | -143.57 | 12.094 | 18679 |
| xmd | xmd1 | A20122 | -561.61 | -11.9 | 81185 |
| xmr | xmr2 | A24219 | -694.387 | -11.583 | 78130 |
| xmr | xmr2 | A22357 | -661.368 | -10.523 | 78745 |
| cwp | cwn2 | A23216 | -10.197 | -10.171 | 78675 |
| cpp | cpp1 | A20313 | -111.374 | -10.148 | 78041 |
| xhr | xhr3 | A16124 | -59.706 | -9.835 | 81629 |
| xmr | xmr2 | A25153 | -703.882 | -9.489 | 81058 |
| xmd | xmd1 | A21194 | -570.91 | -9.3 | 81763 |
| cwn | cwn1 | A16014 | -295.132 | -9.241 | 80135 |
| xgh | xgh1 | A19341 | -181.2 | -9.158 | 67902 |
| xta | xta1 | A17187 | -481.838 | -8.371 | 77411 |
| xmd | xmd1 | A17195 | -542.113 | -8.36 | 81133 |
| xsc | xsc1 | A17341 | -660.241 | -8.271 | 79469 |
| xmm | xmm1 | A16122 | -690.146 | -8.186 | 80523 |
| xgh | xgh1 | A17341 | -155.457 | -8.07 | 81270 |
| xhr | xhr3 | A19325 | -96.28 | -8.07 | 75872 |
| fro | xfro | MON | 7.94 | 7.94 | 18288 |
| xmd | xmd1 | A19195 | -549.705 | -7.595 | 81793 |
| xpk | xpk2 | A16124 | -214.0 | -7.289 | 80817 |
| cpp | cpp1 | A22321 | -136.862 | -7.179 | 70748 |
| xsh | xshh | MON | -47.877 | -7.047 | 19477 |
| c46 | c461 | A13238 | 6.889 | 6.953 | 89152 |
| wkr | wkr1 | A24089 | -471.416 | -6.88 | 81615 |
| wkr | wkr1 | A21159 | -452.693 | -6.877 | 81664 |
| wkr | wkr1 | A26035 | -485.159 | -6.877 | 80636 |
| wkr | wkr1 | A25023 | -478.276 | -6.859 | 81206 |
| wkr | wkr1 | A18087 | -430.484 | -6.845 | 65731 |
| wkr | wkr1 | A20087 | -443.775 | -6.822 | 79880 |
| wkr | wkr1 | A22357 | -459.242 | -6.739 | 78786 |
| wkr | wkr1 | A18233 | -423.797 | 6.687 | 81717 |
| wkr | wkr1 | A21242 | -446.007 | 6.686 | 90685 |
| wkr | wkr1 | A22191 | -452.503 | 6.674 | 81635 |
| wkr | wkr1 | A16122 | -416.917 | -6.664 | 81486 |
| wkr | wkr1 | A16224 | -410.263 | 6.654 | 87702 |
| cpp | cpp1 | A12072 | -72.91 | -6.51 | 86585 |
| c46 | c461 | A23362 | 13.4 | 6.49 | 81617 |
| wkr | wkr1 | A23158 | -464.495 | -5.253 | 78672 |
| cfw | cfw1 | A14144 | -158.82 | 5.231 | 89931 |

## Per-site summary

| site | channel(s) | events | flagged | worst rms | final diff_mm (cumulative) |
|------|-----------|--------|---------|-----------|------------------------------|
| c46 | c461 | 39 | 2 | 0.46 | -53.57 |
| cfd | cfwhi | 3 | 1 | 0.0 | 46.77 |
| cfo | cfwho | 8 | 0 | 0.01 | 29.27 |
| cfw | cfw1 | 49 | 4 | 0.31 | -255.67 |
| chp | chp1 | 47 | 1 | 0.1 | -154.94 |
| coz | coz1 | 52 | 0 | 0.02 | -143.57 |
| cpp | cpp1 | 46 | 4 | 0.26 | -89.19 |
| crr | crr1 | 11 | 4 | 0.32 | -273.23 |
| ctm | ctm1 | 46 | 1 | 0.28 | -137.31 |
| cwc | cwn4 | 8 | 0 | 0.0 | 0.0 |
| cwn | cwn1 | 29 | 0 | 0.02 | -433.983 |
| cwo | cwn3 | 7 | 0 | 0.0 | -3.21 |
| cwp | cwn2 | 8 | 0 | 0.03 | -30.267 |
| frd | xfrd | 7 | 0 | 0.03 | -38.244 |
| fro | xfro | 7 | 0 | 0.0 | 7.94 |
| mee | meed | 12 | 3 | 2.4 | 0.0 |
| meo | meeo | 11 | 1 | 0.09 | 0.0 |
| met | meet | 12 | 5 | 4.44 | 0.0 |
| mrc | xmrc | 12 | 0 | 0.0 | -2.5 |
| mro | xmro | 10 | 0 | 0.07 | -4.26 |
| mrt | xmrt | 12 | 0 | 0.0 | -25.0 |
| nfd | xfrnd | 4 | 3 | 1.96 | 9.717 |
| nfo | xfrno | 3 | 3 | 0.28 | 8.223 |
| sfr | sfrd | 7 | 1 | 3.79 | -14.633 |
| shc | xshco | 8 | 3 | 2.47 | 0.0 |
| shl | xshl | 14 | 0 | 0.0 | 0.0 |
| shr | xshrh | 2 | 1 | 0.0 | 0.0 |
| sht | xsht | 14 | 0 | 0.0 | 0.0 |
| sjb | xsjd | 7 | 0 | 0.0 | -0.45 |
| sjn | sjnh | 12 | 1 | 0.0 | 0.0 |
| wkr | wkr1 | 33 | 1 | 0.14 | -489.836 |
| x46 | x461 | 12 | 0 | 0.01 | 18.71 |
| xgh | xgh1 | 27 | 1 | 0.06 | 0.0 |
| xhr | xhr3 | 33 | 0 | 0.02 | -114.849 |
| xmd | xmd1 | 31 | 2 | 0.01 | -593.93 |
| xmm | xmm1 | 25 | 2 | 0.01 | -778.77 |
| xmr | xmr2 | 17 | 0 | 0.07 | -727.01 |
| xmr2014 | xmr1 | 5 | 2 | 0.09 | -377.38 |
| xpk | xpk2 | 27 | 1 | 0.03 | -276.242 |
| xsc | xsc1 | 22 | 2 | 0.02 | 0.0 |
| xsh | xshh | 8 | 0 | 0.01 | -47.877 |
| xsj | xsj3 | 11 | 0 | 0.04 | -73.02 |
| xta | xta1 | 33 | 3 | 0.11 | 0.0 |
| xva | xva1 | 13 | 11 | 0.71 | -494.89 |
