# SoilMind: An Integrated Representation Learning Framework for Soil Microbial Abundance and Ecological Generalization.

## Project Overview
SoilMind is a research notebook pipeline for integrated ecological AI analysis of soil microbial abundance. The project combines microbial abundance measurements with soil physicochemical variables, climate summaries, spatial coordinates, temporal indicators, and land-cover context in order to study whether learned ecological representations can improve abundance prediction and generalization.

The main notebook in this handover package is:
- `SoilMind_An_Integrated_Representation_Learning_Framework_for_Soil_Microbial_Abundance_and_Ecological_Generalization.ipynb`

## Project Objectives
The codebase supports five main objectives:
1. Build and audit an integrated soil–microbe dataset from multiple ecological sources.
2. Prepare a model-ready ecological dataset with governed features.
3. Establish a frozen ecological benchmark using conventional machine-learning models.
4. Evaluate prediction under stricter validation settings, including grouped-site and time-aware validation.
5. Extend the benchmark with a representation-learning branch based on an autoencoder and latent ecological embeddings.

## Main Workflow
The notebook follows this workflow:
1. Load the integrated SoilMind dataset.
2. Audit columns, data types, missingness, target distributions, and grouping variables.
3. Clean the dataset and save raw, cleaned, and model-ready versions.
4. Train ecological baseline models.
5. Evaluate benchmark performance under random split, 5-fold cross-validation, GroupKFold by site, and time-aware holdout.
6. Compare subgroup-specific performance for fungi and bacteria/archaea.
7. Run interpretability analyses, including SHAP for the fungi benchmark.
8. Run clustering and non-parametric statistical testing for ecological state analysis.
9. Train an autoencoder on the fungi feature matrix and evaluate reduced raw, latent-only, and reduced raw-plus-latent representations.
10. Export final tables, figures, and processed datasets.

## Folder Structure
Recommended package structure:

- `01_source_code/` — notebook, dependency files, and repository link
- `02_data/raw/` — original input files
- `02_data/processed/` — generated cleaned and model-ready datasets
- `03_results/tables/` — exported CSV tables from the notebook
- `03_results/figures/` — exported figures from the notebook
- `04_reproducibility/` — run order, known issues, hardware/runtime notes

## Required Environment
Recommended environment:
- Python 3.10 or 3.11
- Jupyter Notebook, JupyterLab, or VS Code notebook support

Core libraries used in the notebook:
- pandas
- numpy
- matplotlib
- seaborn
- scipy
- scikit-learn
- xgboost
- shap
- torch
- jupyter / notebook / ipykernel

## Installation
Create an environment and install dependencies from `requirements.txt`.

Example:
```bash
python -m venv soilmind_env
source soilmind_env/bin/activate   # Linux/macOS
# or soilmind_env\Scripts\activate on Windows
pip install -r requirements.txt
```

If using Conda, create the environment from `environment.yml`.

## Data Files
The notebook expects a final integrated SoilMind CSV file. In the annotated journal notebook, the code checks `DEFAULT_DATA_PATHS` and uses the first valid file path that exists.

Examples of files referred to in the project:
- `SoilMind_v3_with_coordinates_and_nasa.csv`

Ensure the required CSV is placed in the correct data location before running the notebook.

## How to Run
1. Create and activate the Python environment.
2. Install the dependencies from `requirements.txt`.
3. Place the required dataset file(s) in the expected directory.
4. Open `SoilMind_An_Integrated_Representation_Learning_Framework_for_Soil_Microbial_Abundance_and_Ecological_Generalization.ipynb`.
5. Run the notebook from top to bottom.
6. Check the generated outputs in the notebook output folders.

## Notebook Output Locations
The notebook writes outputs under:
- `content/SoilMind_outputs2/`

Subfolders created by the notebook:
- `figures/`
- `tables/`
- `data/`
- `models/`

Examples of exported tables:
- `dataset_summary.csv`
- `column_inventory.csv`
- `grouping_columns_summary.csv`
- `baseline_model_results.csv`
- `kfold_cv_results.csv`
- `groupkfold_site_results.csv`
- `time_aware_results.csv`
- `subgroup_validation_comparison.csv`
- `clustering_validation_metrics.csv`
- `kruskal_abundance_clusters.csv`
- `final_fungi_shap_importance.csv`
- `feature_governance_table.csv`
- `baseline_benchmark_summary.csv`

Examples of exported figures:
- `missing_values_heatmap.png`
- `raw_meanCopyNumber_distribution.png`
- `log_meanCopyNumber_distribution.png`
- `baseline_feature_importance.png`
- `cluster_abundance_boxplot.png`
- `final_fungi_shap_beeswarm.png`
- `final_fungi_shap_bar.png`
- `ablation_study_r2.png`

## Validation Strategy
The project uses four validation settings:
- Random split
- 5-fold cross-validation
- GroupKFold by site
- Time-aware holdout

These validation regimes are central to the project because they distinguish simple interpolation from stronger ecological generalization.

## Interpretation and Representation Learning
The notebook includes:
- SHAP-based interpretability for the fungi benchmark
- clustering-based ecological state analysis
- a fungi representation-learning branch using an autoencoder
- comparison between reduced raw features, latent-only features, and reduced raw-plus-latent features

## Known Issues
- Local dataset paths may need to be updated depending on the execution environment.
- `xgboost` may require manual installation in some environments.
- `shap` may conflict with some Linux `coverage` installations.
- Representation-learning sections can be memory-intensive.
- Some representation-learning analyses rely on reduced feature approximations for computational feasibility.
- The representation-learning branch is related to, but not a perfectly feature-matched replacement for, the frozen ecological benchmark.

## Contributions
This was a two person project.

Primary data integration and dataset preparation contributions included:
- ecological data identification and alignment
- integrated dataset construction
- model-ready dataset preparation
- missingness checks and feature governance support
- documentation and handover support

Primary AI modelling and evaluation contributions included:
- benchmark model implementation
- subgroup modelling
- strict validation experiments
- representation-learning implementation
- predictive and interpretive analysis

Joint contributions included:
- research question refinement
- interpretation of findings
- thesis/report writing
- final review and handover preparation

## Future Work
Recommended next steps:
- run a strictly matched representation learning experiment using the same ecological feature set as the frozen benchmark
- extend beyond simple autoencoders to denoising or contrastive tabular representation learning
- add uncertainty aware prediction
- expand learned representation experiments beyond fungi
- improve reproducibility through a script-based pipeline in addition to the notebook workflow
- extend the project into a broader benchmark resource for ecological AI
