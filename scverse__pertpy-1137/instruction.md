# Issue

**Title:** Port Milo's GLMM fits to numba

## Description

Fits Milo's random-effect GLMMs in a numba kernel that mirrors the existing algorithm (including bit-exact ports of scipy's Brent searches), taking `da_nhoods` with random effects from ~20 s to ~0.6 s at 200k cells without raising peak memory.
Results move by up to ~1e-5 relative with no significance flips, which is the size of main's own variation across CPU code paths.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b56f68f9e997`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.