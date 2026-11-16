# Issue

**Title:** Compute plot_reg_var_plot variances on sparse X

## Description

`Scgen.plot_reg_var_plot` computes gene variances with `fast_array_utils.stats.mean_var`, so it works on sparse `X` (e.g. after `ad.concat` with a sparse dataset) instead of raising `AxisError`.
Dense input gives the same R² as before.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72498c050719`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.