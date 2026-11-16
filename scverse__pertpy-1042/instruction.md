# Issue

**Title:** Vendor JAX backend for scGen to support scvi-tools 1.5.0

## Description

Fixes scGen import failure under scvi-tools >= 1.5.0.

## Problem

scvi-tools 1.5.0 removed its JAX backend entirely (scverse/scvi-tools#3786), migrating to PyTorch and MLX. pertpy scGen is a JAX/Flax implementation built on that backend, so under scvi-tools >= 1.5.0 importing it fails at module load:

```
ImportError: cannot import name 'JaxTrainingMixin' from 'scvi.model.base'
```

which breaks collection of the whole scGen test module. Everything scGen relied on is gone in 1.5.0: `JaxBaseModuleClass`, `flax_configure`, `scvi.module._jaxvae` (the `flax.struct` `LossOutput`), `JaxTrainingPlan`, `JaxModuleInit`, `JaxTrainingMixin`, and the `return_device="jax"` branch of `parse_device_args`.

## Fix

Rather than pin scvi-tools below 1.5.0, vendor the removed JAX-specific pieces into `pertpy/tools/_scgen/_jax.py`:

- `JaxBaseModuleClass` + `flax_configure`
- `LossOutput` as a `flax.struct.dataclass` (a registered JAX pytree, distinct from the plain dataclass scvi-tools kept) so the loss can be returned from a jitted training step
- `JaxTrainingPlan` (subclasses the still-shipped `scvi.train.TrainingPlan`) and `JaxModuleInit`
- `JaxTrainingMixin`
- a small JAX device resolver replacing the dropped `return_device="jax"` path

Everything still shipped by scvi-tools (`TrainingPlan`, `TrainRunner`, `DataSplitter`, ...) is imported, not copied. The vendored module is faithful to scvi-tools 1.4.0, so scGen behaves identically with no numerical change and no version pin. The docs build also gets `jax.Device` (the public type) and an `annbatch` intersphinx entry so the inherited `setup_annbatch` docstring resolves.

## Testing

- `pytest tests/tools/test_scgen.py` -> 4 passed under scvi-tools 1.5.0.post1
- full pre-commit (ruff, ruff-format, mypy, ...) passes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `89f05aa91ccf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.