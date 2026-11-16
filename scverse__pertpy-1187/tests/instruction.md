# Issue

**Title:** Bump the pre-commit group with 2 updates

## Description

Bumps the pre-commit group with 2 updates: [https://github.com/astral-sh/ruff-pre-commit](https://github.com/astral-sh/ruff-pre-commit) and [https://github.com/zizmorcore/zizmor-pre-commit](https://github.com/zizmorcore/zizmor-pre-commit).

Updates `https://github.com/astral-sh/ruff-pre-commit` from v0.17.0 to 0.17.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff-pre-commit/releases">https://github.com/astral-sh/ruff-pre-commit's releases</a>.</em></p>
<blockquote>
<h2>v0.17.1</h2>
<p>See: <a href="https://github.com/astral-sh/ruff/releases/tag/0.17.1">https://github.com/astral-sh/ruff/releases/tag/0.17.1</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>38bfb07</code></a> Mirror: 0.17.1</li>
<li>See full diff in <a href="https://github.com/astral-sh/ruff-pre-commit/compare/44b5042edab9382aba712eed4f9c7bab7a3d6a3e...38bfb07c0c64c304f47eb52090f8288150c77730">compare view</a></li>
</ul>
</details>
<br />

Updates `https://github.com/zizmorcore/zizmor-pre-commit` from v1.30.1 to 1.31.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/zizmorcore/zizmor-pre-commit/releases">https://github.com/zizmorcore/zizmor-pre-commit's releases</a>.</em></p>
<blockquote>
<h2>v1.31.1</h2>
<p><a href="https://github.com/sponsors/woodruffw/">Sponsorship is appreciated!</a></p>
<h2>Bug Fixes 🐛<a href="https://docs.zizmor.sh/release-notes/#bug-fixes">🔗</a></h2>
<ul>
<li>Fixed a regression in <a href="https://docs.zizmor.sh/release-notes/%5B#1310%5D()">1.31.0</a> where some ignore comments/configurations would no longer apply to the <a href="https://docs.zizmor.sh/audits/#dangerous-triggers">dangerous-triggers</a> audit (<a href="">#2450</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c92afdf</code></a> Mirror: 1.31.1</li>
<li><a href=""><code>d25b2b1</code></a> Mirror: 1.31.0</li>
<li><a href=""><code>04df6d7</code></a> chore: drop Python 3.10 support (EOL) (<a href="">#65</a>)</li>
<li><a href=""><code>fe0957c</code></a> Bump astral-sh/setup-uv from 10.1.0 to 10.2.0 in the github-actions group (<a href="">#64</a>)</li>
<li><a href=""><code>de807da</code></a> Bump the github-actions group with 2 updates (<a href="">#63</a>)</li>
<li>See full diff in <a href="https://github.com/zizmorcore/zizmor-pre-commit/compare/fa412071e4f5d44d44f9e365f4676f9df92456a2...c92afdf2c6ca336aaa8f39e2bd8d48f62dbd8e1f">compare view</a></li>
</ul>
</details>
<br />

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea68f5467e40`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.