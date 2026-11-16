# Issue

**Title:** Fit the guide RNA mixture model by multi-start EM and fix sparse guide assignment

## Description

Fits the Poisson-Gaussian guide mixture by multi-start EM on each guide's distinct count values instead of 500 Adam steps from one start, which left thresholds unconverged, swapped the components on high-MOI guides and dropped small guides; the model and threshold rule are unchanged, results reach the same objective value as crispat run to convergence on all 106 shared Papalexi guides (105 identical thresholds), and the fit is 20x faster at a third of the memory. The threshold methods now accept CSC and sparse-array input (the Papalexi dataset ships as CSC and the documented example failed), explicitly stored zeros no longer enter the fit, `plot_heatmap` saves a reusable cell order, the unused `learning_rate` argument is deprecated, and the tutorial submodule is bumped to the re-executed notebook. Python 3.13 is now required, as anndata main already does, so the test matrix, the mypy hook and the docs build resolve again.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c246f241ba47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.