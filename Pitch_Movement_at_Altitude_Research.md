---
title: "Pitch Movement at Altitude"
subtitle: "A Statcast Study of Rockies Changeups and Home–Road Differences"
date: "October 29, 2026"
author: "Paul J Gornick"
---

**Independent Research Project | Working paper**  
**Study period:** 2015–2026 seasonal exploration; 2024 pitch-level validation  
**Primary outcome:** Absolute horizontal changeup movement, in inches

## Abstract

Coors Field presents an unusual aerodynamic environment for Major League Baseball pitching. This study investigates whether movement changes observed during Colorado Rockies seasons are distinguishable from ordinary year-to-year variation and whether those differences manifest within the same pitcher and season at home versus on the road. A pitcher-season dataset assembled from Baseball Savant exports and MLB team records first identified changes in pitch movement across Rockies and non-Rockies seasons. Eleven pitchers with qualifying adjacent-season changeup comparisons showed less horizontal movement during their Rockies seasons (mean Rockies-minus-other difference: **−2.53 inches**). In 10,000 calendar-year-matched placebo simulations using eligible non-Rockies pitchers, no simulated cohort produced a mean difference as negative; this comparison is exploratory and not a causal significance test. Pitch-level Statcast analyses subsequently found lower horizontal changeup movement at home for all 11 pitchers in that transition cohort. In a separate 2024 Rockies cohort selected on pitch use, **all 10 qualifying pitchers** showed lower movement in designated home games (mean difference: **−3.36 inches**, 95% pitcher-level bootstrap interval **[−3.95, −2.68]**). A 2024 exploratory extension across seven pitch types found lower home movement-vector magnitude in **52 of 53** eligible pitcher–pitch comparisons. The findings support a robust home–road movement association consistent with altitude-related aerodynamics; they do not isolate altitude causally or establish consequences for pitch effectiveness.


<!-- PAPER_PAGE_BREAK -->

## 1. Research question and motivation

The physical conditions in Denver alter the environment through which a baseball travels. A less dense atmosphere can diminish the aerodynamic forces associated with spin, affecting the apparent movement of pitches. Major League Baseball has previously documented lower average pitch movement for Rockies pitchers at home, including changeup arm-side movement during the 2024 season [4]. The purpose of this study is therefore **not** to establish altitude's influence as a new physical discovery. Instead, it is to quantify the consistency of movement differences within pitchers, evaluate whether initial seasonal observations exceed ordinary career variation, and explore how the pattern differs by pitch type.

The analysis developed through three questions:

1. **Seasonal association:** Do pitchers exhibit different movement characteristics in Rockies seasons compared with nearby seasons elsewhere?
2. **Benchmark and attribution:** Are those seasonal differences unusually large relative to normal MLB year-to-year fluctuations, and do they occur within the same Rockies season at home versus on the road?
3. **Pitch-type exploration:** Are home–road movement differences similar across pitch classifications, or do some pitch types retain more of their baseline movement?

The third question is motivated by the distinction between transverse (movement-producing) spin and gyroscopic spin. Gyro spin contributes little directly to Magnus movement, while transverse spin can generate horizontal or vertical aerodynamic deflection [5]. Pitch labels alone, however, do not measure spin efficiency; the present study treats any mechanism-based interpretation as a hypothesis for subsequent investigation.

## 2. Data and analytical design

### 2.1 Seasonal discovery dataset

The initial dataset combines 16 full-season Baseball Savant exports with MLB Statistics API records identifying pitchers who appeared for Colorado. The study covers 2015–2026 and represents pitch type, movement, velocity, spin, usage, and pitcher-season context. After excluding a redundant export and resolving profile issues, the assembled long dataset contains **67,084 pitcher-season/pitch-category records**, representing **9,352 unique pitcher-seasons** and **2,543 pitchers**. Of 335 Rockies pitcher-season records identified through the MLB API, 322 matched the Savant dataset. The unmatched observations were predominantly brief pitching appearances or position-player pitching.

Transitions were formed within pitcher and pitch type, subject to at least **100 plate appearances faced**, at least **5% pitch usage**, and available movement measurements. The primary seasonal comparisons use adjacent calendar years, exclude comparisons spanning the **2019–2020 change in Statcast pitch-tracking systems**, and assign equal weight to each pitcher after averaging repeated transitions of the same pitch [2, 3]. To reduce contamination from traded players, MLB game logs were used to establish Colorado's share of each pitcher's season innings; the strict sample requires **100% of season innings with Colorado**. This restriction does not mean that all pitches were thrown at Coors Field: a Rockies season includes road games.

### 2.2 Pitch-level home–road comparisons

Pitch-by-pitch Statcast data were retrieved using `pybaseball` and MLB identifiers. Regular-season changeups were identified with the `CH` pitch code. The primary 2024 validation sample was selected **before examining home–road movement**: Rockies pitchers had to qualify in the original 2024 season-level data with at least 100 plate appearances faced and 5% changeup usage. A pitcher entered the home–road comparison only when both environments contained at least **20 changeups across at least three games**. Ten of 11 selected 2024 pitchers met these exposure criteria.

`pfx_x`, Statcast's signed horizontal movement measured in feet, was converted to inches by multiplying by 12 [1]. For pitcher *i* in environment *e*, horizontal movement magnitude was defined as **|mean(`pfx_x` × 12)|**. The within-pitcher contrast is **home magnitude minus road magnitude**, so negative values signify less absolute horizontal movement in designated home games. Taking the absolute value removes the directional sign of horizontal movement and can obscure reversals in movement direction. No such reversals occurred among the qualifying 2024 changeup comparisons.

### 2.3 Statistical summaries and exploratory control group

The primary 2024 estimate is the **unweighted mean of 10 within-pitcher home–road differences**. A percentile bootstrap resampled those 10 pitcher-level observations with replacement **20,000 times**, yielding a descriptive 95% interval. The resampling unit is the pitcher, not the pitch.

For the earlier seasonal finding, a non-Rockies reference population contained **1,112 eligible pitchers**, **3,204 eligible changeup pitcher-seasons**, and **1,652 qualifying consecutive-year pairs**. For each of the 11 Rockies pitchers, control candidates were required to possess the same relevant calendar years. Control changes were oriented to match Rockies-minus-other comparisons; repeated events for the same Rockies pitcher were averaged. Ten thousand placebo cohorts were generated by drawing one eligible non-Rockies candidate per Rockies pitcher. These controls matched **calendar-year windows and transition orientation**, but not all pitcher attributes or organizational moves. Results from this post hoc changeup selection are exploratory.

<!-- PAPER_PAGE_BREAK -->

## 3. Results: from seasonal discovery to a control benchmark

### 3.1 Changeups and four-seamers in adjacent seasons

In the strict full-Rockies-season sample, the average induced vertical break for four-seam fastballs was **1.61 inches lower** in Rockies seasons across **25 pitchers**. Horizontal changeup movement showed an even more directionally consistent association: all **11** qualifying pitchers exhibited less movement in their Rockies seasons, with a mean difference of **−2.53 inches** and a median of **−1.80 inches**. After excluding the two largest reductions, the remaining nine still averaged **−1.65 inches**, and all remained negative. The original pitcher-level bootstrap interval was **[−3.85, −1.44] inches**. These patterns motivated the subsequent focus on changeups; they are not evidence that pitch effectiveness declined.

### 3.2 Is the changeup finding ordinary year-to-year variation?

Among eligible non-Rockies pitchers, the median **absolute** consecutive-season change in horizontal changeup movement was **0.80 inches**; the mean absolute change was **1.15 inches**. The 10,000 matched placebo cohorts produced a mean cohort difference near **−0.20 inches**, with the central 95% of simulated cohort means spanning **−1.14 to +0.79 inches**. The observed Rockies mean (**−2.53 inches**) was below every simulated cohort mean. The finite-simulation lower-tail estimate, using a plus-one correction, was approximately **0.0001**. This is a benchmark against a specified control construction, **not** the probability that altitude had no effect and not a confirmatory p-value.

![**Figure 1.** Calendar-year-matched placebo distribution for 11 Rockies pitcher transition profiles. The orange line marks the observed Rockies-minus-other mean (−2.53 in); the teal line is the simulated control expectation (−0.20 in). The shaded region is the central 95% of placebo cohort means.](../figures/figure_3_changeup_control_simulation.png)

The placebo exercise indicates that the observed seasonal reduction is unusual relative to the modeled non-Rockies comparison population. It cannot by itself distinguish altitude from Rockies-specific coaching, pitch-design adjustments, player selection, or other changes. This is why within-season home–road comparisons are the stronger subsequent design.

<!-- PAPER_PAGE_BREAK -->

## 4. Primary result: the 2024 Rockies changeup cohort

The more informative comparison keeps the pitcher, organization, and season constant while contrasting designated Rockies home and road games. An initial 11-pitcher transition cohort showed **less horizontal changeup movement at home for all 11 pitchers**, with an average within-pitcher home-minus-road difference of **−2.98 inches**. Because this cohort had been selected following the seasonal discovery, it was not an independent validation sample.

A separate 2024 roster-based cohort was therefore screened on changeup usage and workload, without reference to its home–road differences. Eleven pitchers were eligible; 10 met the two-environment exposure criteria. Their observed differences were **negative for all 10**. The unweighted pitcher-level mean was **−3.36 inches** (median **−3.28 inches**), and the percentile bootstrap interval was **[−3.95, −2.68] inches**. The mean of pitcher-level percentage differences was **−24.23%**.

![**Figure 2.** Average horizontal changeup movement magnitude for 10 qualifying 2024 Rockies pitchers. Connected points compare Colorado-designated home games (orange) with road games (teal). Every observed home mean is lower.](../figures/figure_1_changeup_home_road.png)

As an illustrative within-pitcher check, **Jon Gray's 2021 changeup** averaged **10.1 inches** of horizontal movement in 113 home changeups across 14 games versus **13.6 inches** in 91 road changeups across 14 games (difference **−3.50 inches**). Resampling at the game level rather than the pitch level produced a 95% bootstrap interval of **[−4.80, −2.12] inches** for this pitcher-season. His average velocity was **87.49 mph at home** versus **87.73 mph on the road** and total spin rate was **1,441 versus 1,476 rpm**, respectively. Those descriptive similarities do not rule out changes in spin axis, spin efficiency, or mechanics, but they make a simple large-velocity explanation less persuasive for this case.

The 2024 results should be described as **Rockies-designated home versus road**, rather than exclusively as Coors Field versus road. Two designated Colorado home games on April 27–28 were played at Estadio Alfredo Harp Helú in Mexico City [6]. The existing analysis retains those games in the home category; the venue exception was identified and documented in the methodological audit, not removed from the final calculations.

<!-- PAPER_PAGE_BREAK -->

## 5. Exploratory extension: seven pitch types

To place the changeup result in context, the same 2024 home–road framework was extended to seven pitch classifications: four-seam fastballs (`FF`), sinkers (`SI`), changeups (`CH`), sliders (`SL`), cutters (`FC`), conventional curveballs (`CU`), and sweepers (`ST`). Seventeen pitchers met the original season-level inclusion criteria, yielding **61 eligible pitcher–pitch combinations**. Fifty-nine comparisons had both home and road measurements; **53** met the minimum 20-pitch/three-game requirement in each environment. **52 of 53** showed reduced movement-vector magnitude at home.

For the broader comparison, the statistic is **sqrt((mean horizontal movement)^2 + (mean induced vertical movement)^2)**, with each component converted to inches. It is the **magnitude of a group's mean movement vector**, not the mean of individual pitches' vector magnitudes, a direct spin-efficiency estimate, or an effectiveness metric. Percent differences were computed at the pitcher–pitch level and then averaged within pitch type.

| Pitch type | n | Mean difference (in) | Mean difference (%) | Less at home |
|:-----------------------------|---:|---------------------:|--------------------:|-------------:|
| Changeup             |       10 |                      −3.69 |          −23.49 |         10/10 |
| Sinker               |        7 |                      −3.93 |          −23.17 |           7/7 |
| Curveball (`CU` only) | 7 |                −2.37 |          −21.64 |           7/7 |
| Four-seam fastball   |       12 |                      −3.55 |          −20.05 |         12/12 |
| Slider               |       10 |                      −1.32 |          −20.01 |         10/10 |
| Sweeper              |        2 |                      −1.74 |          −12.38 |           2/2 |
| Cutter               |        5 |                      −1.14 |          −11.14 |           4/5 |

![**Figure 3.** Individual pitcher–pitch percentage differences (gray points) and pitch-type averages (diamonds), 2024 Rockies home versus road. Sample sizes differ by pitch type.](../figures/figure_2_pitch_type_comparison.png)

Changeups and sinkers exhibited mean reductions of roughly 23%, with reductions across all qualifying pitchers. Cutters showed the smallest mean percentage reduction (approximately 11%), but only **five** cutter observations qualified. Sliders declined by approximately **20%**, nearly the same proportion as four-seam fastballs. Thus, the data do **not** establish a simple relationship in which all slider-family pitches are resilient because of gyro spin. The two sweeper comparisons are particularly limited. Also, `CU` and `KC` are distinct Statcast classifications: two otherwise eligible pitcher–pitch combinations (Kyle Freeland and Austin Gomber) were absent from the `CU` analysis because their breaking balls were labeled `KC` (knuckle curve), rather than `CU`.

<!-- PAPER_PAGE_BREAK -->

## 6. Interpretation and limitations

### 6.1 What the evidence supports

The strongest inference is **descriptive and environmental**: in the studied samples, Rockies pitchers consistently exhibited less horizontal changeup movement in designated home games than on the road during the same season. This design holds pitcher identity and team membership fixed and supports an interpretation involving location-dependent aerodynamics. It does not establish a uniquely Coors-specific causal effect, since opponent mix, ballpark conditions, temperature, humidity, weather, rest, pitch selection and sequencing can differ between home and road appearances.

The seasonal comparisons provide a useful discovery and benchmarking step. They also show why initial team-season averages cannot be equated with the physical impact of altitude: even a 100%-Rockies season includes road starts, and mechanical or pitch-design changes can occur between organizations. The within-season design more directly isolates the location contrast while leaving other home–road differences uncontrolled.

### 6.2 Principal limitations

**Selection and inference.** The original 11-pitcher changeup cohort was chosen after exploring several pitch types, so its subsequent statistical tests are exploratory. The 2024 validation sample was selected by workload and usage without conditioning on its movement outcome, which reduces one form of selection bias but does not make the sample random. Two pitchers appear in both the original and validation cohorts in different seasons; the cohorts are therefore not fully independent.

**Venue definition.** Two Colorado-designated home games in 2024 were played in Mexico City, not Coors Field, and remain coded as home. The principal comparison is accordingly Rockies-designated home versus road, with Coors Field the dominant but not exclusive home venue.

**Measurements and pitch classification.** Statcast reports signed `pfx_x` and `pfx_z` in feet, here converted to inches [1]. The changeup outcome takes the absolute value of mean signed horizontal movement. The seven-pitch metric uses the vector magnitude of mean horizontal and vertical components, which is not a measurement of pure Magnus movement. Because `KC` was not merged with `CU`, the curveball category excludes knuckle curves. Tracking technology changed in 2020; adjacent seasonal transitions spanning 2019–2020 were excluded [2, 3].

**Statistical dependence and uncertainty.** Pitch-by-pitch observations within games are correlated; the main 2024 interval resamples pitchers rather than treating all pitches as independent. In the exploratory seven-pitch summary, several pitch types come from the same pitcher, so the 53 pitcher–pitch records are not 53 independent people. Small cutter and sweeper samples limit comparisons among pitch types. The percentile bootstrap interval is descriptive uncertainty conditional on the observed sample and design; it does not eliminate confounding.

**Outcome scope.** Less movement is not equivalent to worse pitching. The present study does not model whiff rate, called strikes, contact quality, run value, pitch location, injury risk, or team-level pitching development. No direct active-spin efficiency or measured gyro fraction was included. Organizational performance judgments and actionable acquisition rankings are outside the evidence.

### 6.3 Practical implications and next research

A natural next study would combine **pitch-level venue, weather, active-spin estimates, spin direction, seam-shifted-wake indicators, velocity, release characteristics, and pitch effectiveness**. It would compare otherwise similar pitchers and pitches across parks and seasons and directly test whether differences in transverse-spin dependence predict movement retention at altitude. A second step would determine whether movement retention predicts measurable baseball outcomes after accounting for pitch location, tunneling, usage and opposing hitters.

The resulting framework could inform pitcher acquisition and pitch development, but the current results warrant a more restrained conclusion: **Rockies home-game environments are associated with broad reductions in measured pitch movement, and the magnitude appears to differ across pitch types.** Determining which of those differences matters for performance remains an open, baseball-relevant question.

<!-- PAPER_PAGE_BREAK -->

## 7. Reproducibility and research record

The project repository preserves the full chronological Google Colab notebook as the **master research record**, alongside three curated notebooks covering seasonal discovery, changeup validation and home–road comparisons, and the seven-pitch exploratory extension. The notebooks require the original Baseball Savant season exports, MLB Statistics API access and pitch-level Statcast retrieval through `pybaseball`. Results depend on external data services and have not yet been independently re-executed from a completely fresh Colab environment. The paper reports the **audited saved outputs**, not every preliminary estimate in the master notebook.

Audit checks verified that 2024 qualifying changeup results agreed across the independent saved analyses; all 59 calculated pitcher–pitch comparisons reproduced exactly from cached Statcast records; the 2024 exploratory sample comprised 53 qualifying comparisons; and the venue and pitch-code exceptions were identified. Python package versions were recorded in the project's reproducibility audit. No proprietary team data were used.

### References

[1] MLB Baseball Savant. *Statcast Search CSV Documentation.* Defines `pfx_x`, `pfx_z`, pitch codes, game-team fields and measurement units. https://baseballsavant.mlb.com/csv-docs

[2] Major League Baseball. *Statcast.* MLB Glossary. Documents the system's history and the switch to Hawk-Eye in 2020. https://www.mlb.com/glossary/statcast

[3] Major League Baseball. *Pitch-tracking Era (since 2008).* MLB Glossary. Describes TrackMan use through 2019 and Hawk-Eye use beginning in 2020. https://www.mlb.com/glossary/miscellaneous/pitch-tracking-era

[4] Major League Baseball (2025). *How the Colorado Rockies can win consistently at altitude.* Reports home–road movement differences in Rockies pitches, including 2024 changeups. https://www.mlb.com/rockies/news/how-rockies-can-win-consistently-at-altitude

[5] Driveline Baseball (2022). *Basics of Baseball Pitch Movement.* Educational discussion of transverse spin, gyroscopic spin, spin efficiency and movement. https://drivelinebaseball.com/blogs/blog/basics-of-baseball-pitch-movement

[6] Colorado Rockies / MLB. *2024 MLB World Tour: Mexico City Series.* Identifies the April 27–28 Rockies-designated home games played at Estadio Alfredo Harp Helú. https://www.mlb.com/rockies/tickets/mexico-series

---

*Status: Independent working paper; not peer reviewed. Calculations represent the audited project snapshot as of October 29, 2026. No claims are made about causal effects on pitch effectiveness or team coaching quality.*
