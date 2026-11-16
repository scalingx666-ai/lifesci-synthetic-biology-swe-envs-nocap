# Issue

**Title:** Fix import of removed scanpy _get_obs_rep/_set_obs_rep

## Description

## Description

scanpy 1.13.0a1 removed the private helpers `scanpy.get._get_obs_rep` and `scanpy.get._set_obs_rep`, which broke `import pertpy` with:

```
ImportError: cannot import name '_get_obs_rep' from 'scanpy.get'
```

These helpers only resolved `X` vs a named layer, which AnnData handles directly (and `plot_heatmap` in the same file already did inline).
This replaces the imports with direct `adata.X` / `adata.layers[...]` access.

## Testing

`tests/preprocessing/test_grna_assignment.py` passes (23 passed).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6152d326c6a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.