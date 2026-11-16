# Issue

**Title:** Use pooch for dataset downloads

## Description

Drops the custom requests + filelock + retry loop in `_download` and delegates caching, atomic writes, and concurrent-access locking to `pooch.retrieve`. A small `_RichProgress` adapter exposes `rich.progress.Progress` through pooch's tqdm-shaped progressbar protocol, so the existing progress bars are preserved.

The 68 call sites are unchanged — `_download`'s signature stays the same; `max_retries`/`retry_delay` are now no-ops.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `daccc06c06e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.