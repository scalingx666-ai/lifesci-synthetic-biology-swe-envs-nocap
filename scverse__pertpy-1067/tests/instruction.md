# Issue

**Title:** Add discoverability metadata

## Description

Makes pertpy easier to find for search engines, LLM agents and citation tooling.

**PyPI** — adds `keywords` and Issues / Changelog / Forum / Publication project URLs.

**CITATION.cff** — enables GitHub's "Cite this repository" button and lets citation tooling resolve the Nature Methods article. Validated against schema 1.2.0 with `cffconvert`.

**Docs**

- `sphinxext-opengraph` was already a `doc` dependency with `ogp_site_url` and `ogp_image` configured, but was never added to `extensions`. The live docs therefore serve no OpenGraph tags and no meta description at all.
- `html_baseurl` is now taken from `READTHEDOCS_CANONICAL_URL`. Because the build uses custom `build.jobs` commands, Read the Docs does not inject a canonical URL itself, so `/en/latest/`, `/en/stable/` and all nine tagged versions currently compete as duplicate content.
- `docs/llms.txt` is served by Read the Docs from the root of the domain and gives agents a curated map of the API and tutorials. Every symbol it names was checked against `pertpy.tools.__all__`.
- The index page heading now matches the README, so the `<title>` is no longer `pertpy — pertpy`.

`hatch run docs:build` (which passes `-W`) builds clean, and the output contains canonical links, OpenGraph tags and meta descriptions on every page.

Repository topics were separately expanded from 3 to 13 in the repository settings; that is not part of this diff.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f9bb56f87616`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.