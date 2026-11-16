# Issue

**Title:** scCODA/tascCODA: make make_arviz stateless

## Description

- `make_arviz` previously relied on `self.mcmc`, the MCMC object from the last `run_nuts`/`run_hmc` call on the model instance. Looping over datasets and reusing the same model then made `make_arviz(processed_models["region_A"])` blow up with a shape mismatch because `self.mcmc` reflected the last iteration.
- Persist `num_chains` and `extra_fields` alongside the existing posterior samples in `sample_adata.uns["scCODA_params"]["mcmc"]` so an ArviZ DataTree can be rebuilt from the MuData alone via `az.from_dict`. Both `Sccoda.make_arviz` and `Tasccoda.make_arviz` now delegate to a shared helper in `CompositionalModel2`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b321a0cf4bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.