# Issue

**Title:** Densify the Mixscape signature slice before projecting

## Description

`Mixscape.mixscape` now densifies the small cells-by-DE-genes slice before projecting.
`scale=False` works on sparse layers instead of crashing with a dimension mismatch.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `297302443744`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.