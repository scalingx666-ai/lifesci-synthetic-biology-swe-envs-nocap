# Issue

**Title:** Speed up dose-response fits, control differences, MLP training and PubChem lookups

## Description

Adds an analytic Jacobian and `n_jobs` to `fit_dose_response` (2x, ~10x with 10 jobs), numba kernels for `compute_control_diff` (2.4x), chunked `lax.scan` MLP training and throttled parallel PubChem lookups (2.2x).
Everything except the Hill fits is bit-identical; Hill parameters move at optimizer tolerance with no `ec50_in_range` changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8628d501c3b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.