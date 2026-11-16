# Issue

**Title:** Only transfer constant obs columns to pseudobulk

## Description

`PseudobulkSpace.compute` took the first cell's value for every non-grouping `.obs` column, which invents a value whenever a column varies within a group.
It now reuses `_carry_constant_obs` — already backing the other perturbation spaces — so only columns with a single unique value per group are carried over.

`_carry_constant_obs` gained support for multiple grouping columns (for `groups_col`) and now detects constant columns with `groupby.nunique`/`first` instead of a per-group Python callable, which preserves dtypes and is ~5x faster.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `40dfeb6a5a50`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.