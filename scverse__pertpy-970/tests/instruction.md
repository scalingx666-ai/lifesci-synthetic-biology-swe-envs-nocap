# Issue

**Title:** Fix #755: calculate marker positions from DataFrame, not rendered labels

## Description

(merged). Supersedes #966 (closed due to branch recreation during rebase).

#965 fixed the immediate crash by forcing tick labels on, but this still breaks if a user passes `xticklabels=False` via `heatmap_kwargs`. This PR removes the dependency on rendered tick labels entirely.


Before:
![Before](https://gist.githubusercontent.com/kimjune01/bf4f7f7d89a816d34bff1708a0cce935/raw/after.png)

After:
![After](https://gist.githubusercontent.com/kimjune01/bf4f7f7d89a816d34bff1708a0cce935/raw/before.png)


Changes:
- Calculate marker positions directly from DataFrame structure (cell centers at 0.5, 1.5, ...) instead of extracting from rendered plot
- Works regardless of label visibility, figsize, or gene count
- Add comment noting that positioning assumes non-clustered heatmap
- Update test to reproduce the original bug (50 genes + small figsize) and test with explicitly hidden labels

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8ed067094a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.