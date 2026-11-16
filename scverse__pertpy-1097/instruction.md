# Issue

**Title:** Add native Hill dose-response fitting

## Description

Adds `fit_dose_response` and `plot_dose_response`, which fit and plot a four-parameter Hill curve per perturbation for the distance or any gene, storing EC50 and the curve parameters in `.obs`.
`dose_response` now returns a perturbation-by-dose AnnData with mean expression in `X` instead of a DataFrame, which is a breaking change to the 1.2.0 API.
Companion tutorial: scverse/pertpy-tutorials#77.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8820e3c8739`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.