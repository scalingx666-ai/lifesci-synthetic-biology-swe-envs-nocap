# Issue

**Title:** Keep adjusted p-values when some simple-test p-values are NaN

## Description

`TTest`, `WilcoxonTest` and `PermutationTest` returned NaN for every `adj_p_value` as soon as one variable had a NaN p-value, e.g. a gene without variance.
BH is now applied to the tested variables only, so adjusted p-values are available again on typical single-cell data.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1047baf3e3b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.