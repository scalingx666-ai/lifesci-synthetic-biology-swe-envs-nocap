# Issue

**Title:** Colour the docs' sidebar captions with pertpy's logo red

## Description

The docs now take both accents from the scverse-doc registry: the logo blue as before, and the logo red for the sidebar captions via `secondary_accent`.
Waits for scverse/scverse-doc#73 and the release after scverse-doc 0.2.4, whose minimum version this PR still has to bump.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ba19dbb8876`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.