# Issue

**Title:** Show output filename in download progress

## Description

<!-- Many thanks for contributing to this project! -->

**PR Checklist**

<!-- Please fill in the appropriate checklist below (delete whatever is not relevant). These are the most common things requested on pull requests (PRs). -->

-   [x] Referenced issue is linked
-   [ ] If you've fixed a bug or added code that should be tested, add tests!
  - No new automated test was added because this is a presentation-only change to the progress description.

**Description of changes**

Dataset download progress now includes the output filename instead of displaying the same generic `Downloading...` description for every dataset.

For example:

```text
Downloading replogle_2022_k562_essential.h5ad ━━━━━━━━━━ 100% 0:00:00
Downloading norman_2019.h5ad ━━━━━━━━━━ 100% 0:00:00
```

This makes sequential dataset downloads easier to distinguish

 

**Technical details**

`output_file_name` is passed to `_RichProgress` when constructing the `pooch.HTTPDownloader`:
```python
progressbar=_RichProgress(description=f"[red]Downloading {output_file_name}")
```

This does not change the download behavior, public API, dependencies, or dataset contents.

Validation:
- uv run pytest -k "not EdgeR": 577 passed, 3 skipped, 17 deselected
- uv run pre-commit run --files pertpy/data/_dataloader.py
- git diff --check
EdgeR tests were excluded because the local environment does not have a working R installation. The failures observed when running them were unrelated to this change.

**Additional context**

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08a10510eea6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.