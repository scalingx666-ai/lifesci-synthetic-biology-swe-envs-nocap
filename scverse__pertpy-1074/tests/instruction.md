# Issue

**Title:** Bump the pre-commit group with 3 updates

## Description

Bumps the pre-commit group with 3 updates: [https://github.com/biomejs/pre-commit](https://github.com/biomejs/pre-commit), [https://github.com/astral-sh/ruff-pre-commit](https://github.com/astral-sh/ruff-pre-commit) and [https://github.com/zizmorcore/zizmor-pre-commit](https://github.com/zizmorcore/zizmor-pre-commit).

Updates `https://github.com/biomejs/pre-commit` from v2.5.5 to 2.5.6
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>cd5d6ed</code></a> build(deps): bump <code>@​biomejs/biome</code> to 2.5.6</li>
<li><a href=""><code>4c53f19</code></a> build(deps): bump <code>@​biomejs/biome</code> to 2.5.5 (<a href="">#120</a>)</li>
<li>See full diff in <a href="https://github.com/biomejs/pre-commit/compare/06894e75c7c22ab408daf8e1ad00c2fe81512f08...cd5d6ed44598e228e214b704d673541d9675f8e4">compare view</a></li>
</ul>
</details>
<br />

Updates `https://github.com/astral-sh/ruff-pre-commit` from v0.16.0 to 0.16.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/ruff-pre-commit/releases">https://github.com/astral-sh/ruff-pre-commit's releases</a>.</em></p>
<blockquote>
<h2>v0.16.1</h2>
<p>See: <a href="https://github.com/astral-sh/ruff/releases/tag/0.16.1">https://github.com/astral-sh/ruff/releases/tag/0.16.1</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>39d9ac5</code></a> Mirror: 0.16.1</li>
<li><a href=""><code>299cd31</code></a> Bump actions/checkout from 7.0.0 to 7.0.1 in the github-actions group (<a href="">#177</a>)</li>
<li>See full diff in <a href="https://github.com/astral-sh/ruff-pre-commit/compare/cb8c523fd4835aba42af70f4cad5568db4df0b6c...39d9ac5938dadb73df0564a45f163e25ff9fa6e2">compare view</a></li>
</ul>
</details>
<br />

Updates `https://github.com/zizmorcore/zizmor-pre-commit` from v1.28.0 to 1.29.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/zizmorcore/zizmor-pre-commit/releases">https://github.com/zizmorcore/zizmor-pre-commit's releases</a>.</em></p>
<blockquote>
<h2>v1.29.0</h2>
<h2>New Features 🌈<a href="https://docs.zizmor.sh/release-notes/#new-features">🔗</a></h2>
<ul>
<li>
<p>zizmor now has <strong>experimental</strong> support for auditing pre-commit inputs, meaning both pre-commit configuration and hook definitions (<a href="">#2209</a>)</p>
</li>
<li>
<p>New audit: <a href="https://docs.zizmor.sh/audits/#insecure-url-scheme">insecure-url-scheme</a> detects usages of insecure (i.e. plaintext) protocols when making network requests. The initial version of this audit is limited to pre-commit inputs only (<a href="">#2228</a>)</p>
</li>
<li>
<p>zizmor now supports GitHub's &quot;self-repository&quot; reference syntax for local actions, e.g. <code>uses: $/foo/bar</code> instead of a manual checkout and <code>uses: ./foo/bar</code> (<a href="">#2248</a>)</p>
</li>
</ul>
<h2>Changes ⚠️<a href="https://docs.zizmor.sh/release-notes/#changes">🔗</a></h2>
<ul>
<li>The <a href="https://docs.zizmor.sh/audits/#unpinned-uses">unpinned-uses</a> and <a href="https://docs.zizmor.sh/audits/#unpinned-images">unpinned-images</a> audits have been separated more cleanly: <a href="https://docs.zizmor.sh/audits/#unpinned-uses">unpinned-uses</a> is now principally responsible for Git-style <code>uses:</code> clauses, whereas <a href="https://docs.zizmor.sh/audits/#unpinned-images">unpinned-images</a> is now responsible for <code>docker://</code>-style <code>uses:</code> clauses (in addition to already checking other image references) (<a href="">#2222</a>)</li>
</ul>
<h2>Removals 🌅<a href="https://docs.zizmor.sh/release-notes/#removals">🔗</a></h2>
<ul>
<li><code>--collect=workflows-only</code> and <code>--collect=actions-only</code> have been fully removed. Use <code>--collect=workflows</code> and <code>--collect=actions</code> for the replacement behavior (<a href="">#2242</a>)</li>
</ul>
<h2>Bug Fixes 🐛<a href="https://docs.zizmor.sh/release-notes/#bug-fixes">🔗</a></h2>
<ul>
<li>
<p>Fixed a bug where zizmor would reject a valid workflow definition for containing a literal jobs.<!-- raw HTML omitted -->.outputs.<!-- raw HTML omitted --> value for being a non-string (<a href="">#2220</a>)</p>
</li>
<li>
<p>Fixed a bug where the <a href="https://docs.zizmor.sh/audits/#github-app">github-app</a> audit would incorrectly flag some usages as needing a repositories: key, despite requesting organization-level-only permissions (<a href="">#2227</a>)</p>
</li>
<li>
<p>Fixed a class of bugs where zizmor would discover the user's configuration in unintuitive ways. When auditing from a Git repository, zizmor now uses the repository root to discover configuration consistently (<a href="">#2234</a>)</p>
</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>451b56a</code></a> Mirror: 1.29.0</li>
<li><a href=""><code>c7cc406</code></a> Use upstream zizmor release notes for releases (<a href="">#51</a>)</li>
<li><a href=""><code>8f87f00</code></a> Bump the github-actions group with 3 updates (<a href="">#54</a>)</li>
<li>See full diff in <a href="https://github.com/zizmorcore/zizmor-pre-commit/compare/067260dc5fe6ea86b7551bfd6f8b3ba4e6c93129...451b56af716f9f0d0c2b816503a3fd0cf8b036fa">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c429c58229a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.