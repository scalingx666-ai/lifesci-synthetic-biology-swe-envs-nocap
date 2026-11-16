# Issue

**Title:** Keep permutation p-values aligned with their group labels in DistanceTest

## Description

.

The null distribution is stored per permutation in alphabetical order while the observed distances keep the order of appearance of `adata.obs[groupby]`.
Counting the failures went through a bare numpy array, which dropped the labels, and the counts were then reattached positionally to the order of appearance, so groups whose two orders differ received each other's p-values.
Both `test_xy` and `test_precomputed` now share `_permutation_pvalues`, which stays in pandas and reindexes onto the observed order, so the array that `multipletests` returns is positional against the right groups as well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `557813ceb0f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.