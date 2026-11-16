# Issue

**Title:** Resolve scgen test warnings

## Description

Three warning categories from `test_scgen`:

- `_scgen.py:248-249`: writing to `.X` on a view of a view. Now `.copy()` the per-batch view first, then mutate. Matches the original (no-op for `temp_cell`) semantics — the second write-back was already discarded into a transient view, mirroring upstream scGen.
- `_scgen.py:266` / `:289`: `corrected[adata.obs_names]` returns a view; the subsequent `obsm["latent"] = ...` actualises it. Added `.copy()` after the slice.
- 10× `UserWarning: Observation names are not unique`: `balancer` oversamples with replacement, producing duplicate obs_names that cascade into every downstream `_check_if_view`/`copy`. Made them unique inside `balancer`, suppressed the unavoidable warning during the intermediate slice, and passed `index_unique="-"` to the eval concat in the test.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6aee8b74cf5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.