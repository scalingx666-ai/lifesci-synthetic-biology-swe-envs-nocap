# Issue

**Title:** Drop empty annotation rows from plot_da_beeswarm

## Description

.

The row order was derived from `nhood_adata.obs` before the `"nan"` annotations were filtered out and with the pandas default of `observed=False`, so annotation categories without any neighbourhood were drawn as empty rows.
The order now comes from the plotted frame with `observed=True`, which also makes the plot independent of the pandas version -- the default flipped to `True` in pandas 3.0, so this only shows up for users on pandas 2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `557813ceb0f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.