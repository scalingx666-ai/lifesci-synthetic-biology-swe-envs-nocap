# Issue

**Title:** Fix plot_effects_umap KeyError on Sccoda output

## Description

Should resolve #780.

`summary_prepare` in `_base_coda.py` renames the first effect column differently per `select_type`:
- `"sslasso"` branch (Tasccoda) → `"Effect"` (line 602)
- else branch (Sccoda) → `"Final Parameter"` (line 616)

`plot_effects_umap` hardcoded `"Effect"` at line 2211, so calling it on Sccoda output crashed with `KeyError: 'Effect'`. The rest of the file already handles this divergence — for example, lines 904-917 branch on `select_type` to pick the correct column name.

This wraps the lookup so it picks `"Effect"` if present, otherwise `"Final Parameter"`. Behavior on Tasccoda is unchanged.

Also adds a regression test `test_plot_effects_umap_sccoda` that fits a small Sccoda model and confirms `plot_effects_umap` no longer crashes. Locally verified — full `tests/tools/_coda/` suite passes (6 pass, 1 pre-existing skip).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8ed067094a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.