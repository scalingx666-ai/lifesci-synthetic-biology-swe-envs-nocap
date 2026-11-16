# Issue

**Title:** Apply scGen batch_removal's latent correction and align obsm["latent"]

## Description

Restores scGen `batch_removal`'s per-batch latent shift, which #982 accidentally discarded, and reindexes `obsm["latent"]` to `adata.obs_names` so latent rows match their cells.
`batch_removal` output changes accordingly, since it previously decoded the uncorrected latent.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc0c235585ad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.