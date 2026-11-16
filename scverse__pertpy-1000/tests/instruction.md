# Issue

**Title:** perturbation_space: skip None-keyed layers in _combine

## Description

## Summary
- `sc.get.aggregate` can leave a `None`-keyed layer on the returned AnnData.
- `PseudobulkSpace.compute` already strips it (added in #976), but the `_combine` refactor in #994 introduced `key.endswith("_control_diff")` calls that crash on a stray `None` key — which is what the CI failure on `test_linear_operations` was hitting.
- Filter to string keys before doing the string ops and the iteration that builds the new AnnData, with a comment so this doesn't regress next time someone touches `_combine`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d49818655489`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.