# Issue

**Title:** Speed up hot loops without changing results

## Description

Hoists loop invariants and vectorizes per-element Python loops in scGen, scCODA, Enrichment, DistanceTest, Milo, Mixscape, Distance and CINEMA-OT.
Outputs are exactly equal to main, with speedups of up to ~340x on the affected functions (e.g. scGen `balancer` 11.6 s to 0.03 s, scCODA `from_scanpy` 19 s to 0.13 s at 200k cells).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47016a14a995`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.