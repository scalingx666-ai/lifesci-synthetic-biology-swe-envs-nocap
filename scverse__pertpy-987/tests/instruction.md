# Issue

**Title:** Guide RNA assignment: crispat-matching JAX MAP fit (10–30× faster)

## Description

Replaces the MCMC-based Poisson-Gaussian mixture in `GuideAssignment.assign_mixture_model` with a JAX/optax MAP fit that mirrors [`crispat.ga_poisson_gauss`](https://github.com/velten-group/crispat) (same priors, same continuous-Poisson likelihood, same `P(Normal | log2(t)) > 0.5` thresholding, same skip rules). All guides are fit in one batched `jax.vmap` + `jax.lax.scan` pass; per-guide MAP estimates match crispat to ~4 decimal places.

### Head-to-head, 2000 cells × 30 simulated guides (10% true positives)

| Method | Time | Accuracy | Sensitivity | Specificity | TP | FP | FN |
|---|---:|---:|---:|---:|---:|---:|---:|
| pertpy (new, JAX MAP) | **3.25 s** | 0.9995 | 0.9954 | 1.0000 | 6111 | 0 | 28 |
| crispat (Pyro SVI) | 35.23 s | 0.9995 | 0.9954 | 1.0000 | 6111 | 0 | 28 |
| pertpy (old, NumPyro NUTS) | 85.65 s | 0.6823 | 0.2305 | 0.7338 | 1415 | 14336 | 4724 |

Same model, same assignments as crispat — but one batched JIT pass instead of a per-guide Python loop.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d75da25d2f79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.