# Release Manifest

Archive purpose: focused release package for the Bayesian analysis used in the
Chapter 2 tillage impacts on water quality manuscript and a future
Zenodo-citable repository. Version 2.1 (`v2p1`) is the final selected Bayesian
workflow for formal inference in this archive.

## Included Source Code

- `code/run_pipeline.py`
- `code/wq_longify.py`
- `code/stir_pipeline.py`
- `code/merge_wq_stir_by_season.py`
- `code/merge_residue.py`
- `code/stir_bayes_backend.py`
- `code/stir-bayes-backend.R`
- `code/stir-bayes-load2p1_nonneg.Rmd`
- `code/m_stir_mogp_v2p1.stan`

## Included Data Inputs

- `data/Master_WaterQuality_Kerbel_LastUpdated_10272025.csv`
- `data/tillage_records.csv`
- `data/tillage_mapper_input.csv`
- `data/crop records.csv`
- `data/residue_2011_2025.csv`
- `data/STIR_values_MOSES_2023_data.csv`
- `data/methods.csv`

## Included Outputs

- Final Bayes-ready input: `out/wq_cleaned.csv`
- Pipeline intermediate CSVs under `out/pipeline_csvs/`
- Final v2p1 Bayesian annual load, study-period load, annual volume, and
  mapping audit outputs
- Final v2p1 Bayesian figures under `figs/`

## Included Documentation

- Release README: `README.md`
- Pipeline documentation: `docs/README_data_pipeline.md`
- Bayesian methods documentation: `docs/README_bayes_methods.md`
- v2p1 unit-of-analysis notes: `docs/README_bayes_methods_v2p1_notes.md`
- Model version summary: `docs/bayes-model_versions.md`
- STIR calculation documentation: `docs/STIR calculations.md` and `.pdf`
- License: `LICENSE`

## Notes

v2p1 is the final and selected Bayesian model for formal inference. Users
reproducing the analysis should run the v2p1 driver and Stan model.
