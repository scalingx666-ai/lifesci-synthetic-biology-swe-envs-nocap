# Issue

**Title:** perturbation_space: cleanup, safer defaults, kill stale-state bugs

## Description

## Summary
Code-quality pass on \`pertpy.tools._perturbation_space\`. Net **-45 lines** across the module while addressing all of the structural issues I had on the list. Public class names and method signatures stay intact — only two *default values* change (called out below). All existing tests pass.

## What changed

### Structural / DRY
- \`compute_control_diff\`: collapse the **four** duplicated per-mask subtraction loops (X, layer, embedding, all_data extras) into one \`_subtract_control_mean\` helper. Previously the primary paths fell back to zeros when a group had no control cells, but the all_data extras silently produced NaN with a \`RuntimeWarning\` — now both branches take the same code path and emit one explicit warning.
- \`add\` / \`subtract\`: deduplicate ~100 lines of copy-paste into a single \`_combine\` backend that takes the operator (\`+=\` / \`-=\`). The \`_control_diff\` suffix → original-name mapping is now an explicit rename dict, so a user layer literally called \`foo_control_diff\` no longer gets mangled by \`str.removesuffix\` round-trips.
- \`KMeansSpace\` / \`DBSCANSpace\`: shared \`_run_clustering\` helper. The two classes are now ~10 lines each.
- New \`_resolve_matrix\` / \`ClusteringSpace._resolve_coords\` helpers — single source of truth for the "layer wins over embedding wins over .X" rule.

### Correctness
- **\`ClusteringSpace\` no longer smuggles \`self.X\` from \`compute()\` to \`evaluate_clustering()\`.** That was the worst bug in the module: results depended on call order, and reusing one instance across two datasets silently mixed them. \`evaluate_clustering\` now takes \`layer_key\` / \`embedding_key\` and resolves coordinates the same way \`compute\` does.
- **\`CentroidSpace.compute\` closest-centroid lookup** is now vectorized (\`np.argmin(np.linalg.norm(points - centroid, axis=1))\`). The old \`min(points, key=lambda ...)\` ran a Python-level loop over a numpy matrix.
- **\`CentroidSpace.compute\` dead branch** removed — there was a branch reachable only when both \`layer_key\` and \`embedding_key\` were \`None\` that then indexed \`adata.obsm[embedding_key]\` (i.e. \`adata.obsm[None]\`).
- **\`PseudobulkSpace.compute\` no longer mutates the caller's \`adata.obs[target_col]\`** when called with \`embedding_key=None\` — the categorical cast happens on the internal shadow now, not the input.

### Default changes (small behaviour break, intentional)
- \`compute_control_diff(copy=False)\` → \`copy=True\`. The old default silently mutated caller-owned \`.layers\` / \`.obsm\` / \`.X\`.
- \`add(ensure_consistency=False)\` / \`subtract(ensure_consistency=False)\` → \`True\`. The old default produced a geometrically inconsistent space and emitted a warning literally saying \"Run with \`ensure_consistency=True\`\". The unsafe mode is still reachable by passing the flag explicitly (e.g. when the caller has already differenced the input).

### Cleanup
- \`label_transfer\` no longer has the undocumented \`kwargs.pop(\"column\")\` back-compat shim.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a857e644e0e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.