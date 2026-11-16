# Issue

**Title:** Fix PseudobulkSpace.compute losing X with anndata main

## Description

In anndata main, `layers` exposes a virtual `None` key aliased to `.X`. The previous order set `X = layers[mode]` then `del layers[None]`, which deleted X via the alias. `psadata.obsm["X_umap"] = psadata_umap.X` then stored `None`, breaking the later `adata.copy()` in `compute_control_diff`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3defe41447c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.