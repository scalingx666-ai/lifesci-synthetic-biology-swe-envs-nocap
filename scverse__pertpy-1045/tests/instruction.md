# Issue

**Title:** Update template to v0.8.0

## Description

> [!NOTE]
> **Curated by a maintainer.**
> The auto-generated branch was based on a pre-template commit and conflicted heavily with `main`.
> It has been rebuilt on top of current `main` to include only the parts of the v0.8.0 update that apply cleanly to pertpy.

### Included

- **GitHub Actions supply-chain hardening** across all workflows: actions pinned to commit SHAs (version kept as comments for dependabot), `persist-credentials: false` on every checkout, and least-privilege `permissions:` blocks.
- **`.github/dependabot.yml`** (github-actions ecosystem) to keep the pins updated.
- **zizmor** pre-commit hook + biome `.cruft.json` exclude.
- `codecov-action` OIDC upload, "list installed package versions" CI step, and `continue-on-error` for pre-release test environments.
- **Template version handling**: dropped the `__version__`/`__author__`/`__email__` dunders from `pertpy/__init__.py` and removed the inert `[tool.hatch.version] source = "vcs"` block. The static `[project].version` already drives the build (verified unchanged at `1.1.1`); consumers use `importlib.metadata.version("pertpy")`.
- `.cruft.json` bumped to v0.8.0.

`zizmor` passes with no findings.

### Intentionally skipped (pertpy has diverged here)

- The `docs/conf.py` overhaul, sphinx-tabs→sphinx-design, and `scverse_misc.sphinx_ext` — pertpy's docs config is heavily customized and already uses sphinx-design and depends on `scverse-misc`.
- `.gitkeep` files and the `.yaml` / `.readthedocs.yaml` / `.codecov.yaml` filename churn — pertpy uses `.yml` deliberately and the content is identical.

---

<details>
<summary>Original template-update description</summary>

`cookiecutter-scverse` released [v0.8.0](https://github.com/scverse/cookiecutter-scverse/releases/tag/v0.8.0).

## Changes

This release comes with a bunch of smaller fixes and changes to the template, and a lot of under-the-hood changes reducing friction with template sync and initialization.

## Changes

The most notable change is the introduction of [zizmor](https://github.com/zizmorcore/zizmor) as pre-commit hook for hardening github actions against supply-chain attacks. Github actions will be pinned to an immutable hash instead of a version number. Dependabot will take care of updating them (by `@ilan-gold`, `@grst`, `@ilia-kats` in ).

Additionally, we introduced a helper package, [scverse-misc](https://github.com/scverse/scverse-misc), that contains utility code shared across scverse core and ecosystem packages. As an initial step, we moved custom sphinx extensions that were previously part of the template into scverse-misc (by `@ilia-kats` in ). Rollout of additional features (shared logging and settings) will follow in the next release.

The remaining changes are listed below:

## Updates to the template

 * ci: remove hacks for docs building by `@flying-sheep` in
 * ci: list all installed packages in CI output by `@grst` in
 * ci: bump codecov-action to v6 to fix signature verification by `@timtreis` in
 * feat: remove __version__ cargo cult by `@flying-sheep` in
 * docs: update instructions on hatch/VScode integration by `@grst` in
 * docs: sphinx 9 compatibility, sphinx-tabs→sphinx-design by `@flying-sheep` in
 * docs: use the official readthedocs badge in README by `@ilia-kats` in
 * docs: robust links by `@flying-sheep` in
 * docs: recommend prek over pre-commit by `@ilia-kats` in  and by `@grst` in
 * docs: recommend uv for installation (alternative) by `@grst` in
 * docs: fix typo by `@ilan-gold` in

## Template sync, docs, and initialization (changes do not affect instance repos)

* Fix docs on migrating to the template by `@grst` in
* Add docs link to PR comment by `@flying-sheep` in
* Fix cruft changing .git and add info on manual template update by `@moinfar` in
* Improve PyPI release instructions in template_usage.md by `@grst` with `@Copilot` in
* Switch to github app for PR creation by `@grst` in
* Do not trigger cruft workflow on pre-releases by `@grst` in
* add contents:read permission to test workflow by `@ilia-kats` in
* Take up template sync where it got interrupted by `@grst` in
* Escape GitHub `@mentions` in template update PR bodies by `@grst` with `@Copilot` in
* Do not mandate global git config by `@grst` in
* fix: template sync no longer breaks from multiple choice options by `@grst` in
* fix: mention casing in publisher docs by `@flying-sheep` in
* Allow user to choose between issue type and labels by `@grst` in

## Additional remarks
* **unsubscribe**: If you don’t want to receive these PRs in the future,
  add `skip: true` to [`template-repos.yml`][] using a PR or,
  if you never want to sync from the template again, delete the `.cruft.json` file in the root of your repository.
* If there are **merge conflicts**, you need to resolve them manually.
* The scverse template works best when the [pre-commit.ci][], [readthedocs][] and [codecov][] services are enabled.
  Make sure to activate those apps if you haven't already.

[`template-repos.yml`]: https://github.com/scverse/ecosystem-packages/blob/main/template-repos.yml
[pre-commit.ci]: https://cookiecutter-scverse-instance.readthedocs.io/page/template_usage.html#pre-commit-ci
[readthedocs]: https://cookiecutter-scverse-instance.readthedocs.io/page/template_usage.html#documentation-on-readthedocs
[codecov]: https://cookiecutter-scverse-instance.readthedocs.io/page/template_usage.html#coverage-tests-with-codecov

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `473b6ad2315a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.