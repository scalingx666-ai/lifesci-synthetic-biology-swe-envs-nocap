# Issue

**Title:** Make JAX scGen reproduce PyTorch scGen

## Description

## Summary

pertpy's JAX scGen has never faithfully reproduced the canonical PyTorch scGen ([theislab/scgen](https://github.com/theislab/scgen)). Diffing the JAX module against the canonical source turned up **three concrete divergences**, all fixed here:

1. **Reconstruction loss reduced over the wrong axis (the dominant bug).**
   ```python
   # before — sums over the ENTIRE minibatch → scalar
   return jnp.sum((x - px) ** 2)
   # after — per cell, sum over genes → vector [batch], matching scGen's .sum(dim=1)
   return jnp.sum((x - px) ** 2, axis=-1)
   ```
   With `loss = mean(0.5 * rl + 0.5 * kl * kl_weight)`, the old scalar `rl` scaled with `batch_size`, dwarfing the KL term and making the objective batch-size dependent.

2. **Decoder was missing batch norm.** Canonical `DecoderSCGEN` uses scvi `FCLayers` (default `use_batch_norm=True`) and `SCGENVAE` runs with `use_batch_norm="both"`. pertpy built `FlaxDecoder` without passing `use_batch_norm`, so it defaulted to `False`. Now the decoder honors `use_batch_norm`/`use_layer_norm` like the encoder.

3. **Encoder did not add `var_eps`.** scvi's `Encoder` adds `var_eps=1e-4` to the latent variance; the Flax encoder now does too.

The architecture otherwise already matched (n_hidden=800, n_latent=100, n_layers=2, dropout=0.2, LeakyReLU, BN momentum/eps).

## Verification

- **Offline numerical parity:** with identical parameters and inputs, the module's training loss now equals the canonical scGen objective recomputed by hand — `6.5323769911546…` vs `6.5323769911546…`, matching to ~15 significant digits.
- The end-to-end train → `batch_removal` → `predict` → reg-mean/var pipeline still runs.

## Tests

Added three regression tests (no new dependency) pinning each fix:
- `test_scgen_reconstruction_loss_is_per_cell` — reconstruction loss has shape `(n_cells,)`.
- `test_scgen_decoder_uses_batch_norm` — the decoder has `BatchNorm` params under `use_batch_norm="both"`.
- `test_scgen_encoder_applies_var_eps` — the encoder adds `var_eps` to the variance.

## Note

This **changes outputs for existing users** — intentionally, since the prior behavior did not reproduce scGen.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eaea364938d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.