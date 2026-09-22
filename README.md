# setter-attack-distribution-volleyball

Decision-based indicators (unpredictability & diversity) for evaluating volleyball setters' tactical decision-making, using CatBoost modeling and Delphi expert validation on KOVO V-League play-by-play data.

# Setter Decision-Making Index (Volleyball)

This repository contains the data pipeline, modeling code, and analysis scripts supporting a research study that develops and validates two decision-based indicators — **unpredictability** (Brier Score, derived from a CatBoost attack-zone classification model) and **diversity** (Shannon entropy of attack-option distribution) — as a process-oriented complement to the conventional set-success rate metric for evaluating professional volleyball setters.

Using play-by-play data from all 126 regular-season matches of the 2025-26 Korean V-League (KOVO), independent variables for the predictive model were derived and validated through a modified Delphi survey (N=20 experts). The analysis includes discriminant validity testing, bootstrapped mediation analysis (examining blocker count as a mediating pathway to attack success), and a composite ranking index weighted by Delphi-derived importance ratings.

## Repository Structure

- `data/df_final_with_metrics.csv` — Preprocessed dataset with computed indicators
- `src/dvw_batch_pipeline.py` — .dvw scouting file parser (built on [pydatavolley](https://github.com/openvolley/pydatavolley))
- `notebooks/analysis_full.ipynb` — Full analysis pipeline (model training, indicator computation, mediation analysis, Delphi validation)
- `requirements.txt`
- `README.md`
- `LICENSE`

## Methods Overview

- **Data parsing**: `dvw_batch_pipeline.py` — batch parser for .dvw scouting files, built on [pydatavolley](https://github.com/openvolley/pydatavolley)
- **Modeling**: Attack-zone classification via CatBoost (compared against Random Forest and XGBoost baselines)
- **Indicators**: Brier Score (unpredictability) and Shannon entropy (diversity) computed with bootstrapped confidence intervals
- **Mediation analysis**: Blocker count examined as a mediating pathway to attack success
- **Expert validation**: Modified Delphi survey (N=20 experts), including CVR/CVI validation and Delphi-derived importance weighting for the composite ranking index

## Data Availability

This repository includes only the preprocessed dataset used in the analysis (`data/df_final_with_metrics.csv`), containing rally-level attack distribution and outcome variables derived from the raw scouting files. The original scouting files (.dvw) are not released, in accordance with the data provider broadcaster's policy.

## How to Run

1. Install dependencies: `pip install -r requirements.txt`
2. Run the parsing pipeline: `python src/dvw_batch_pipeline.py`
3. Open `notebooks/analysis_full.ipynb` to reproduce the full analysis, including model training, indicator computation, and mediation analysis.

## Citation

If you use this code or methodology, please cite the associated research paper (details to be added upon publication).
