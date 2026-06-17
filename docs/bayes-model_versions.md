# Model Versioning Summary

**Kerbel Long-Term Tillage Impacts Project**  
**AJ Brown**

This document tracks the structure and diagnostic status of Bayesian load-model
versions used in the STIR-water-quality analysis workflow. Each version
corresponds to a specific R Markdown driver file and Stan implementation.

Version 2.1 (`load2p1`) is the final selected model for formal inference in
this repository.

---

## Load Models (Volume + Concentration) - Current

**Current selected model:** `load2p1`

**Stan file:** `code/m_stir_mogp_v2p1.stan`

**Driver file:** `code/stir-bayes-load2p1_nonneg.Rmd`

**Status:** **FINAL SELECTED VERSION - used for formal inference**

| Version | File | Key structural features | Diagnostic status | Notes |
| --- | --- | --- | --- | --- |
| 1.0 | load1p0 | Posterior load computation from separate concentration and volume models | Converged | Initial integrated load workflow |
| 1.1 | load1p1 | Joint concentration-volume structure; inflow imputation | Converged | First unified volume + concentration model |
| 1.2 | load1p2 | MVN priors; non-centered parameterization | Converged | Improved sampling geometry |
| 1.3 | load1p3 | Single-output Gaussian process over year | Converged | Temporal smoothing introduced |
| 1.4 | load1p4 | Multi-output GP across analytes | Converged | Cross-analyte temporal structure |
| 1.5 | load1p5 | CmdStan standardization; annual load summaries | Converged | Production-ready pipeline |
| 1.6 | load1p6 | Stable multi-output GP baseline | Converged | Baseline reference model |
| 1p7 | load1p7 | Introduced latent true states for volume and inflow; expanded hierarchy | Did not converge | Severe divergences and treedepth saturation |
| 1p7p1 | load1p7p1 | Simplified latent structure; retained crop and residue | Did not converge | Geometry instability persisted |
| 1p7p2 | load1p7p2 | Additional reparameterization attempts | Did not converge | Poor mixing; E-BFMI failures |
| 1p7p3 | load1p7p3 | Refined covariance and hierarchical structure | Did not converge | Persistent divergences |
| 1p7p4 | load1p7p4 | Pre-final restructuring before full stabilization | Did not converge | Parameterization still unstable |
| 1p7p5 | load1p7p5 | Finalized latent-state formulation; stabilized non-centered parameterization; full MOGP; analyte-specific crop, residue, and irrigation effects | Converged | Previous selected model |
| 1p8 | load1p8 | Added explicit concentration censoring via left-censored likelihood, inflow-volume (`VIN`) imputation, updated residue submodel using previous crop, and retained stabilized latent-state + MOGP structure | Converged | Superseded by v2p1; retained for lineage |
| **2p1** | **load2p1** | Retains the earlier nonnegative workflow and scientific structure, but models outflow volume once per volume-measurement event, VIN once per physical plot event, and residue once per planting-season plot unit before mapping shared values back to analyte rows | **Final selected version** | Corrects analyte-row pseudo-replication and is the version used for formal inference. First completed run had 54 divergences, one chain with E-BFMI 0.267, and 9 research-facing parameters with R-hat > 1.01; report these diagnostics with the analysis. |

---

## Clarification On Earlier Versions

Versions `1p7` through `1p7p4` introduced expanded latent-state structures and
additional hierarchy but failed to satisfy convergence diagnostics. These
models are retained in the development record only and are not used for
inference or reporting.

Version `1p7p5` resolved prior geometric pathologies through:

- fully non-centered latent truth parameterization;
- stabilized multi-output Gaussian process structure;
- corrected covariance factorization;
- improved missing-data integration; and
- removal of unstable parameter couplings.

Version `1p8` extended `1p7p5` by preserving the stabilized geometry while
adding:

- explicit concentration censoring via row-level reporting-limit thresholds;
- missing inflow-volume (`VIN`) imputation;
- the residue submodel using previous-crop effects on logit residue proportion;
  and
- posterior predictive quantities for concentration, volume, and residue.

Version `1p8` satisfied convergence diagnostics and was the selected analysis
model before the v2p1 unit-of-analysis correction. It is retained in this
repository only for Bayesian model lineage and is not the selected formal
inference version.

Version `2p1` is the final selected workflow. It corrects analyte-row
pseudo-replication for volume-measurement-event outflow volume, physical
plot-event VIN imputation, and planting-season residue likelihood/imputation.
Its first completed run converged better than the row-replicated formulation,
but retained 54 divergences, one chain with E-BFMI below 0.3, and 9
research-facing parameters with R-hat above 1.01. These diagnostics should be
reported transparently. v2p1 is nevertheless the final selected model for
formal inference in this repository because it uses the corrected unit of
analysis.

---

## Concentration Models - Historical

These were early standalone concentration models before integration into the
joint load framework.

| Version | File | Description | Status |
| --- | --- | --- | --- |
| 1.0 | conc1p0 | Multi-analyte concentration regression | Historical |
| 1.1 | conc1p1 | Added DAG-motivated structure | Historical |

---

## Volume Models - Historical

| Version | File | Description | Status |
| --- | --- | --- | --- |
| 1.0 | vol1p0 | Standardized volume regression on STIR | Historical |

---

## Notes For Future Updates

- Add a new row for each version created.
- Record diagnostic status explicitly.
- Do not describe planned features as implemented features.
- The selected model for inference must always be clearly labeled.
- If a newer version changes the data interface, such as censoring inputs or
  imputation indices, note that explicitly in the table.
