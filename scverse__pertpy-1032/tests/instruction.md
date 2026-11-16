# Issue

**Title:** Rework perturbation spaces around a perturbation-level API

## Description

Reworks `pertpy`'s perturbation space module so that every space returns one observation **per perturbation** and the spaces compose with each other, and adds distance/embedding spaces plus combination and dose analyses.

- `MLPClassifierSpace` averages its penultimate-layer activations per perturbation (was one embedding per cell).
- Classifiers default to `target_col="perturbation"` and emit the label under `target_col` with perturbation-named `obs_names`, so `classifier → distance/cluster/neighbors` chains work.
- Reproducible `random_state` accepting `int | Generator | RandomState | None` (new `RandomStateLike` in `pertpy/_types.py`).
- Sparse-aware `JAXDataset` (per-batch densification), shared obs-carry helpers, and typing cleanup (`str | None`, dropped `# type: ignore`s).
- **`DistanceSpace`** — wraps `Distance.pairwise` into a perturbation space (matrix in `.X` and `.obsp["distances"]`), feeding clustering/neighbors directly.
- **`PerturbationSpace.nearest_perturbations`** — rank perturbations by proximity (mechanism-of-action lookup).
- **`PerturbationSpace.plot_similarity`** — clustered heatmap of perturbation distances.
- **`EmbeddingSpace`** — ingest an external per-perturbation embedding (e.g. scGPT/Geneformer gene embeddings).
- **`evaluate_combinations`** — score an additive model (`effect(A)+effect(B)`) against the measured combination effect.
- **`dose_response`** — effect size of each perturbation versus dose.
- `DBSCANSpace` → **`HDBSCANSpace`** (sklearn `HDBSCAN`).

## Breaking changes (clean break, no shims)
- Classifier `target_col` default `"perturbations"` → `"perturbation"`; output column follows `target_col` instead of the hardcoded `"perturbations"`.
- `MLPClassifierSpace` returns perturbation-level (not cell-level) embeddings.
- `DBSCANSpace` removed in favor of `HDBSCANSpace`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31b2fe926d39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.