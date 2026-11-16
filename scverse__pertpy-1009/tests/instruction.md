# Issue

**Title:** ci: bump codecov-action to v6 and fail CI on upload error

## Description

Two changes to every codecov upload step in this repo:

1. **codecov-action -> `@v6`.** Versions below 6.0.2 verify the codecov CLI binary against Codecov's old Keybase key, which they bricked after migrating accounts, so uploads now fail with `Could not verify signature`. `@v6` (= 6.0.2) ships the updated key.
2. **`fail_ci_if_error: true`.** Matches the `cookiecutter-scverse` template default so a broken upload fails CI loudly instead of passing silently.

Ref:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0a81cc661e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.