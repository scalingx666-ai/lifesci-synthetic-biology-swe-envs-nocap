# Issue

**Title:** Fit Dialogue's random-intercept models with a numba kernel

## Description

Replaces Dialogue's per-gene statsmodels MixedLM fits with a numba maximum-likelihood random-intercept fit, taking `test_celltype_pairs` from 119 s to 0.9 s at 30k cells with unchanged peak memory.
P-values shift slightly (median 0.8% relative, no significance flips) because the kernel converges where statsmodels' default BFGS stops early; program genes and scores are unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b56f68f9e997`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.