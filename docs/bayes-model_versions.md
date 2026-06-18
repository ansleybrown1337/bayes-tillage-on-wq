# Model Version Summary

**Kerbel Long-Term Tillage Impacts Project**  
**AJ Brown**

Version 2.1 (`v2p1`) is the final selected Bayesian load model for formal
inference in this repository.

## Final Selected Model

**Model version:** `load2p1`

**Stan file:** `code/m_stir_mogp_v2p1.stan`

**Driver file:** `code/stir-bayes-load2p1_nonneg.Rmd`

**Primary dataset:** `out/wq_cleaned.csv`

**Status:** final selected version used for formal inference.

## Scope

The v2p1 model jointly represents runoff concentration and runoff volume,
propagates uncertainty into event and annual loads, and accounts for missing
concentration, inflow concentration, inflow volume, outflow volume, and residue.

The model uses the corrected unit of analysis for shared variables:

- outflow volume is modeled once per volume-measurement event;
- inflow volume is represented once per physical plot runoff event; and
- residue is modeled once per planting-season plot unit.

These event-level and residue-unit quantities are mapped back to analyte rows
for concentration modeling, load calculations, and downstream summaries.

## Diagnostic Note

The first completed v2p1 run finished on June 14, 2026 and produced the final
Bayesian outputs included in this repository. That run had:

- 54 divergent transitions across 4,000 post-warmup draws;
- no maximum-treedepth transitions;
- one chain with E-BFMI below 0.3 (`0.267`);
- 9 research-facing parameters with R-hat above 1.01; and
- worst research-facing R-hat: `1.141`.

These diagnostics should be reported transparently with the analysis. They do
not change the repository versioning decision: v2p1 is the final selected model
for formal inference.
