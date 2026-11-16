# Issue

**Title:** Fit linear mixed models with a random intercept in the differential expression interface

## Description

.
`pt.tl.Statsmodels` fits a linear mixed model when the design contains a random intercept such as `~condition + (1 | donor)`, by REML with Satterthwaite t-tests that match `lmerTest`, so single cells can be tested while accounting for the samples they come from.
The kernel is shared with Dialogue and no longer spawns nested parallel regions, which makes both the new fits and Dialogue's cell type tests several times faster.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4df75ac52e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.