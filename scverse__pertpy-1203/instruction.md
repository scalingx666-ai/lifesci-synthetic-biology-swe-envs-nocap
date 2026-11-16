# Issue

**Title:** Bump the pre-commit group with 2 updates

## Description

Bumps the pre-commit group with 2 updates: [https://github.com/biomejs/pre-commit](https://github.com/biomejs/pre-commit) and [https://github.com/zizmorcore/zizmor-pre-commit](https://github.com/zizmorcore/zizmor-pre-commit).

Updates `https://github.com/biomejs/pre-commit` from v2.6.3 to 2.6.4
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>eb45ebf</code></a> build(deps): bump <code>@​biomejs/biome</code> to 2.6.4</li>
<li><a href=""><code>9a227f8</code></a> build(deps): bump <code>@​biomejs/biome</code> to 2.6.3 (<a href="">#135</a>)</li>
<li>See full diff in <a href="https://github.com/biomejs/pre-commit/compare/f9fccc969fb42a59a17a1a430df9f38851f9b2da...eb45ebf3cb7c3a872b3ff0814883e8ab81fc451f">compare view</a></li>
</ul>
</details>
<br />

Updates `https://github.com/zizmorcore/zizmor-pre-commit` from v1.31.1 to 1.32.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/zizmorcore/zizmor-pre-commit/releases">https://github.com/zizmorcore/zizmor-pre-commit's releases</a>.</em></p>
<blockquote>
<h2>v1.32.0</h2>
<p><a href="https://github.com/sponsors/woodruffw/">Sponsorship is appreciated!</a></p>
<h2>New Features 🌈<a href="https://docs.zizmor.sh/release-notes/#new-features">🔗</a></h2>
<ul>
<li>zizmor now has experimental support for GitHub Actions workflow lockfiles. Please see <a href="https://docs.zizmor.sh/usage/#workflow-lockfiles">the limitations documentation</a> for more information about the current implementation and its limitations (<a href="">#2463</a>)</li>
</ul>
<h2>Enhancements 🌱<a href="https://docs.zizmor.sh/release-notes/#enhancements">🔗</a></h2>
<ul>
<li>
<p>zizmor's input collection is now &quot;root-aware&quot; by default, meaning that invocations like zizmor . will no longer collect inputs unless they would actually be used by GitHub Actions, etc. This should eliminate spurious findings from (e.g.) workflow definitions in vendored directories. See the <a href="https://docs.zizmor.sh/usage/#input-collection">input collection</a> documentation for more information. (<a href="">#2454</a>)</p>
</li>
<li>
<p>zizmor's LSP now honors the didChangeWorkspaceFolders event (<a href="">#2461</a>)</p>
</li>
<li>
<p>zizmor's LSP now audits pre-commit inputs (<a href="">#2485</a>)</p>
</li>
<li>
<p>zizmor now provides Windows ARM64 wheels on PyPI (<a href="">#2424</a>)</p>
<p>Many thanks to <a href="https://github.com/ndabas"><code>@​ndabas</code></a> for proposing and implementing this improvement!</p>
</li>
</ul>
<h2>Bug Fixes 🐛<a href="https://docs.zizmor.sh/release-notes/#bug-fixes">🔗</a></h2>
<ul>
<li>
<p>Fixed a bug where the <a href="https://docs.zizmor.sh/audits/#bot-conditions">bot-conditions</a> audit did not properly flag if: condition of jobs that call a reusable workflow (<a href="">#2457</a>)</p>
</li>
<li>
<p>Fixed a bug where the <a href="https://docs.zizmor.sh/audits/#obfuscation">obfuscation</a> audit would incorrectly flag (and suggest an incorrect auto-fix for) expressions that constant-reduce to other expressions (<a href="">#2483</a>)</p>
</li>
<li>
<p>Fixed a bug where the <a href="https://docs.zizmor.sh/audits/#template-injection">template-injection</a> audit did not flag attacker-controllable contexts wrapped in fromJSON(...), such as fromJSON(toJSON(github.event.issue.title)) (<a href="">#2495</a>)</p>
</li>
<li>
<p>Fixed a bug where the <a href="https://docs.zizmor.sh/audits/#template-injection">template-injection</a> audit did not flag attacker-controllable contexts in the values of case(...), such as case(cond, github.event.issue.title, 'x') (<a href="">#2504</a>)</p>
</li>
<li>
<p>Fixed a class of bugs in the <a href="https://docs.zizmor.sh/audits/#obfuscation">obfuscation</a> audit where a constant-reducible subexpression would not be replaced with a contextually correct form (<a href="">#2483</a>)</p>
</li>
<li>
<p>Fixed a bug where zizmor would incorrectly audit pre-commit inputs that ended with .yml, despite pre-commit requiring the .yaml suffix (<a href="">#2485</a>)</p>
</li>
<li>
<p>Fixed a bug where zizmor would not honor some ignore comments for the <a href="https://docs.zizmor.sh/audits/#stale-action-refs">stale-action-refs</a> audit (<a href="">#2494</a>)</p>
</li>
<li>
<p>Fixed a bug where zizmor would not honor some ignore comments for the <a href="https://docs.zizmor.sh/audits/#ref-version-mismatch">ref-version-mismatch</a> audit (<a href="">#2494</a>)</p>
</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>06a3975</code></a> Mirror: 1.32.0</li>
<li>See full diff in <a href="https://github.com/zizmorcore/zizmor-pre-commit/compare/c92afdf2c6ca336aaa8f39e2bd8d48f62dbd8e1f...06a39750ec31860bb44f2acf67182c40016cd1e7">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3279fad7dc05`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.