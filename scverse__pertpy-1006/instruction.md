# Issue

**Title:** Fix all-NaN extra obs after PseudobulkSpace with groups_col

## Description

## Summary
- .
- When `PseudobulkSpace.compute` was called with `groups_col`, every obs column not produced by `sc.get.aggregate` (e.g. `Efficacy`, `Treatment`) came out all-NaN. The per-group lookup is a `MultiIndex(target_col, groups_col)`, but it was being reindexed against `ps_adata.obs.index`, which is the joined `"target_groups"` string index — so nothing matched.
- The downstream symptom is the empty-index design matrix that `DeseqDataSet` rejects: with all-NaN factors, formulaic drops every row.
- Fix: reindex the per-group lookup using the grouping columns themselves (single `Index` when there is one grouping col, `MultiIndex.from_frame` when there are two), then re-attach `ps_adata.obs.index`.
- Added a regression test that asserts the extra obs column is preserved when `groups_col` is set.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0a81cc661e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.