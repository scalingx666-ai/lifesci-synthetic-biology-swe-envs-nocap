# Issue

**Title:** Save the binary guide assignment matrix of the mixture model as a layer

## Description

Stacked on #1172. `assign_mixture_model` now also writes the full cell-by-guide binary assignment to `adata.layers[output_layer]` (default `assigned_guides`, sparse for sparse input, like `assign_by_threshold`), because the per-cell string in obs is capped at `max_assignments_per_cell` guides and joins names with a separator, which loses information in high-MOI designs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72eb8524b35f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.