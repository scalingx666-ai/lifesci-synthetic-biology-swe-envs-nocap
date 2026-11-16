# Issue

**Title:** Build the docs with scverse-doc

## Description

Switches the docs to the shared scverse theme and configuration from `scverse-doc`, as anndata and scanpy did, which removes most of `conf.py` and the dead `docs/_ext` extensions. The logo blue is now set once as the theme accent in `conf.py`, which derives the link and hover colors for light and dark mode, while the red sidebar captions stay in CSS.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a76171e76ba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.