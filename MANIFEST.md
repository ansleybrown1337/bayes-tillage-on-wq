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
- Historical Bayesian lineage files retained for traceability:
  - `code/stir-bayes-load1p8_nonneg.Rmd`
  - `code/m_stir_mogp_v1p8.stan`

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

## Excluded From The Full Development Repository

This repository intentionally contains only the Bayesian analysis release
materials needed to reproduce the v2p1 formal-inference workflow. Broader
development materials, non-Bayesian project components, superseded Bayesian
archives, compiled Stan executables, saved fit objects, CmdStan run
directories, local IDE metadata, R session files, and temporary files are
excluded.

## Notes

v2p1 is the final and selected Bayesian model for formal inference. Earlier
v1p8 source files are retained only as historical lineage because v2p1 builds
from that workflow while correcting the unit of analysis for volume, VIN, and
residue. Users reproducing the analysis should run the v2p1 driver and Stan
model.
