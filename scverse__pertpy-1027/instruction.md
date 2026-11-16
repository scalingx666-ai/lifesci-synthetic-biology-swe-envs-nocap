# Issue

**Title:** Deduplicate metadata download boilerplate

## Description

## Summary

The identical download-and-cache block (build the cache path, skip if the file is already present, `_download` from the pertpy example-data server) was repeated **seven times** in `_cell_line.py` and again in `_moa.py` and `_drug.py`.

This PR extracts it into a single `MetaData._download_metadata` staticmethod, sitting next to the existing `_warn_unmatch` helper on the shared superclass:

```python
_BASE_URL = "https://exampledata.scverse.org/pertpy"

@staticmethod
def _download_metadata(file_name: str) -> Path:
    """Download a metadata file into scanpy's cache directory if absent and return its path."""
    path = Path(settings.cachedir) / file_name
    if not path.exists():
        _download(url=f"{MetaData._BASE_URL}/{file_name}", output_file_name=file_name,
                  output_path=settings.cachedir, block_size=4096)
    return path
```

Each `_download_*` method drops from ~12 lines to 2–3, and the base URL / cache-skip logic now lives in one place.

## Details

- The **pharmgkb** branch in `_drug.py` stays inline on purpose: it downloads a zip and renames the extracted file, with the existence check on a *different* file than the one downloaded, so folding it into the generic helper would change behavior.
- Collapsed the threefold source dispatch in `Drug.annotate` / `Drug.lookup` now that the lazy-load is uniform.
- Removed the now-unused `Path` / `settings` / `_download` imports from `_cell_line.py` and `_moa.py`.

Net change: **+92 / −159** in the metadata package.

## Tests

Added network-free unit tests (`tests/metadata/test_metadata.py`) for the new helper: the existing metadata tests cover downloads end-to-end but require the network, and the refactor moved URL construction into one spot that now affects *every* download. The new tests mock `_download` and assert (a) the URL is built from the base and (b) a cached file is not re-fetched.

The full `tests/metadata/` suite (12 tests, real downloads) passes locally, confirming the refactor is behavior-preserving across all sources.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `473da9260e7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.