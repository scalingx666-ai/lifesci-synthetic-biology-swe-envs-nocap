# Issue

**Title:** Keep Milo's per-sample obs index unnamed for pandas 3.1

## Description

With pandas 3.1, the per-sample obs index that Milo builds kept the sample column's name, so `plot_nhood_counts_by_cond` raised on an ambiguous merge key.
The index is now unnamed again, which fixes the milo tutorial.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1a442c9a824`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.