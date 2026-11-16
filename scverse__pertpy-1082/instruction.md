# Issue

**Title:** Add signature reversal scoring to enrichment

## Description

**PR Checklist**

- [x] Referenced issue is linked
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Documentation in `docs` is updated

**Description of changes**

This adds a first CMap-style signature reversal workflow to `pt.tl.Enrichment`.

Given perturbation-level `AnnData` with perturbations as observations and genes as variables, users can provide either up/down query gene sets or a signed query signature. The method scores each perturbation by how strongly it opposes the query signature and stores the results back on the AnnData object.

This addresses the signature reversal part of #1036. It does not address Bliss/Loewe synergy, dose-response, or genetic interaction workflows.

**Technical details**

- adds `Enrichment.signature_reversal`
- stores reversal score, connectivity score, and rank in `adata.obs`
- stores query metadata and result keys in `adata.uns`
- supports `.X`, an optional layer, and optional gene-symbol matching through `adata.var`
- documents signature reversal under the Enrichment tools section
- adds compact tests for up/down gene sets and signed query signatures
- adds no new dependency

**Testing**

- `ruff check src\pertpy\tools\_enrichment.py tests\tools\test_enrichment.py`
- `ruff format --check src\pertpy\tools\_enrichment.py tests\tools\test_enrichment.py`
- `pytest tests\tools\test_enrichment.py -q -p no:cacheprovider`

Addresses part of #1036.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `61428d5a87aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.