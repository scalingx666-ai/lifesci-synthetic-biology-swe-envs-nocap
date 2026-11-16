# Issue

**Title:** docs: refresh DE docstring pseudobulk examples

## Description

## Summary
Two small docs-only changes tied together by issue #615:

1. **DE docstring examples**: refresh the `Examples` blocks in `pertpy/tools/_differential_gene_expression/_base.py` (5 occurrences across `EdgeR`/`PyDESeq2` plot and `compare_groups` docstrings) so they use the current `PseudobulkSpace.compute(...)` signature. The previous examples passed the long-removed `min_cells=10`/`min_counts=1000` kwargs, so anyone copy-pasting them hit `TypeError: compute() got an unexpected keyword argument 'min_cells'`. Reported by @mschilli87 in #615.
2. **Intersphinx**: add `decoupler` to `docs/conf.py`'s `intersphinx_mapping` so MyST cross-references like `{func}` ``~decoupler.op.collectri`` `` (introduced in the companion tutorials PR scverse/pertpy-tutorials#60) resolve to decoupler's docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f93ff82ceef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.