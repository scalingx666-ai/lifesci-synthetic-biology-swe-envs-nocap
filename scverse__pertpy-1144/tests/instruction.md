# Issue

**Title:** Apply fixed covariances in MixscapeGaussianMixture's M-step

## Description

`MixscapeGaussianMixture` now recomputes its precisions from the fixed covariances, so the NT component's variance is actually held at the NT sd during EM, as in Seurat's mixscape.
Before, only the fixed mean was used; on synthetic screens this changes the KO/NP call for at most ~1% of guide cells.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e63c5d0c51f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.