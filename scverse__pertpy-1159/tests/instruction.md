# Issue

**Title:** Accept hdi_prob in scCODA summaries with arviz 1.x

## Description

`summary_prepare` and `summary` accept `hdi_prob` again and forward it to arviz 1.x as `ci_prob` with `ci_kind="hdi"`, and HDI columns are labelled `HDI X% lower/upper` like the ETI ones.
The documented `sccoda.summary(mdata, hdi_prob=0.8)` call no longer raises `TypeError`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b60d21bb682`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.