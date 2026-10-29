Pitch Movement at Coors Field
Author: Paul J Gornick

Independent baseball analytics research project. This repository includes the complete original Google Colab research notebook as the master research record, three curated notebooks for easier reading, and three figures exported from the analysis. The master is an exact, unedited copy of the uploaded notebook. The curated notebooks preserve the existing methods and displayed results, but have not been re-executed from a clean Colab runtime.
Full research paper
[Read the research paper (PDF)](Pitch_Movement_at_Altitude_Research.pdf) · [Editable Word version](Pitch_Movement_at_Altitude_Research.docx) · [Markdown source](Pitch_Movement_at_Altitude_Research.md)

The paper contains the methodology, three figures, audited results, limitations, and opportunities for future research. The published paper should be treated as the narrative reference for final claims, while the original notebook remains the chronological research record.
Key results
- Primary, usage-selected 2024 changeup cohort: 10 qualifying Rockies pitchers, all showing lower horizontal changeup movement magnitude in designated home games than road games; mean home minus road −3.36 inches; 95% pitcher-level bootstrap interval [−3.95, −2.68] inches.
- Seasonal exploratory changeup comparison: 11 pitchers with Rockies/non-Rockies neighboring seasons had a mean difference −2.53 inches. Calendar-year-oriented placebo simulations using non-Rockies pitchers had a mean near −0.20 inches; 0 of 10,000 simulated cohorts had an average as negative as the observed value. This is exploratory, not a causal probability.
- 2024 seven-pitch-type extension: 53 qualifying pitcher-pitch observations across 17 pitchers; 52 showed lower overall movement-vector magnitude in designated Rockies home games. Different pitches from the same pitcher are not independent.
Movement differences do not by themselves demonstrate loss of pitch effectiveness. Home-versus-road associations do not establish that altitude alone causes the differences.
Master notebook and research lineage
[00 — Master full research notebook](00_master_full_research.ipynb) is the unedited, chronological record of the project, including exploratory tests, intermediate findings, methodological audits, and plotting work. Keep it unchanged so the project's development and decisions remain traceable; do not treat every exploratory result within it as a final claim.

The three notebooks below are curated presentations of that work, intended to help reviewers follow the reproducible workflow without reading every investigation in the master notebook. The audited final-result CSVs and the explicitly qualified findings in this README / research paper should determine the numbers reported publicly if an exploratory cell differs. Changes to analytical methods should be made in a clearly versioned follow-up, not silently edited into the master record.
Curated notebook execution order
1. 01_seasonal_discovery.ipynb — source imports, player-season master data, team-transition sample, movement calculations. Requires the original sixteen Baseball Savant full-season CSV exports in a Google Drive folder, named exactly as the code expects.
2. 02_changeup_validation.ipynb — matched placebo simulations, individual-pitch Statcast home/road retrieval, 2024 changeup validation, and bootstrap interval.
3. 03_pitch_types_audit_and_figures.ipynb — seven-pitch-type extension, integrity checks, and the three paper figures.
At the top of each notebook, edit PROJECT_DIR to the folder holding your Baseball Savant exports and generated CSV files. The default is /content/drive/MyDrive/Coors Project. Run cells top-to-bottom in Google Colab. The original computations rely on the MLB Stats API and pybaseball for retrieving additional data; they require network access. These notebooks are sequenced but not self-contained: Notebook 02 needs the outputs of 01, and Notebook 03 needs those of 01 and 02. Data and API results may differ from the preserved notebook outputs if upstream data changes.

Captured environment from the research audit: Python 3.13.18, pandas 2.2.3, numpy 2.1.3, scipy 1.16.3, matplotlib 3.10.0, requests 2.32.4, pybaseball 2.2.7. The package does not ship the raw Savant exports or Statcast caches; they remain in the researcher's Google Drive.
Figures

Important methodological notes
- Venue: Two Colorado-designated home games in 2024 were played at Mexico City's Estadio Alfredo Harp Helú, not Coors Field. The existing figures retain these as Rockies home games. Therefore label findings designated Rockies home vs road and explicitly note this exception. Do not claim every included home pitch was at Coors.
- Curveball definition: CU (conventional curveball) is included; KC (knuckle curve) is not grouped into the curveball category. The audit identified KC records for Kyle Freeland and Austin Gomber, explaining two eligible-but-unmatched CU observations.
- Movement measures: Horizontal changeup movement is the absolute value of mean signed horizontal break. In the exploratory seven-pitch analysis, two-dimensional movement is sqrt((mean pfx_x*12)^2 + (mean pfx_z*12)^2); this is the magnitude of the mean movement vector, not the mean per-pitch magnitude. Statcast pfx_x and pfx_z are in feet.
- Sample rules: For the 2024 validation, at least 20 pitches and at least 3 games in each environment. Data are grouped by pitcher before estimating the primary changeup confidence interval.
- Control analysis: Non-Rockies pitchers are calendar-year matched, but not perfectly matched on changes in velocity, pitch design, age or organizational environment. Changeups were investigated after exploratory pitch-type screening; significance results are exploratory.
- Spin mechanism: Pitch names do not provide direct active-spin or gyro-spin measurements. Any statement about gyro resilience is a hypothesis for future analysis rather than a demonstrated causal result.
- Scope: This project does not estimate run value, pitcher quality, pitch effectiveness, or the isolated causal contribution of altitude.
Reproducibility status
The master notebook preserves the complete research record, and the three curated notebooks organize the workflow. The curated notebooks have not yet been executed end-to-end in a fresh Colab runtime. The original 16 Baseball Savant CSV exports and pitch-level Statcast caches are not distributed in this repository; anyone reproducing the analysis must obtain the source exports, configure PROJECT_DIR, and retrieve public MLB API / Statcast data. The reported figures and paper reflect the audited research snapshot. A clean-runtime reproduction remains future work.
