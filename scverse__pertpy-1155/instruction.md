# Issue

**Title:** Tolerate duplicate obs_names in Mixscale's DE grouping

## Description

Mixscale's DE step raised `InvalidIndexError` on screens with duplicate `obs_names` since #1140.
It builds the control and perturbed groups from `isin` masks again, which tolerates repeated barcodes and leaves results for unique names unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f60cc1c2b58`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.