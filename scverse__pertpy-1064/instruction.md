# Issue

**Title:** Correct the version of the Milo deprecations

## Description

1.0.7 was never released — the tags go from 1.0.6 straight to 1.1.0 — so the rendered deprecation notices for `subset_samples` and `add_covariate_to_nhoods_var` pointed at a version nobody can have installed.
Both shipped in 1.1.0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71b576168764`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.