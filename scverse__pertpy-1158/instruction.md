# Issue

**Title:** Carry obs columns that are NaN for some groups onto pseudobulks

## Description

`PseudobulkSpace.compute` dropped every obs column that was NaN for any group, although its docstring promises to carry over all columns that are constant within each group.
Metadata missing for a few cell lines (e.g. `Age`, `SangerModelID`) is now carried over as NaN for those groups instead of disappearing, which the metadata annotation tutorial relies on; this reverses the earlier test expectation that such columns are dropped.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72498c050719`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.