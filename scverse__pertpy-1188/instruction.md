# Issue

**Title:** Bump the actions-deps group with 3 updates

## Description

Bumps the actions-deps group with 3 updates: [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv), [pypa/gh-action-pypi-publish](https://github.com/pypa/gh-action-pypi-publish) and [actions/setup-python](https://github.com/actions/setup-python).

Updates `astral-sh/setup-uv` from 10.3.0 to 10.3.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/setup-uv/releases">astral-sh/setup-uv's releases</a>.</em></p>
<blockquote>
<h2>v10.3.1 🌈 preserve cache error class names in save-cache bundle</h2>
<h2>Changes</h2>
<p>This release includes a fix so that multiple concurrent workflows trying to upload the same cache no longer warn</p>
<p><code>##[warning]Failed to save: Unable to reserve cache with key ..., another job may be creating this cache.</code></p>
<h2>🐛 Bug fixes</h2>
<ul>
<li>fix: preserve cache error class names in save-cache bundle <a href="https://github.com/dannyward630"><code>@​dannyward630</code></a> (<a href="">#1093</a>)</li>
</ul>
<h2>🧰 Maintenance</h2>
<ul>
<li>chore: update known checksums for 0.13.4 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1099</a>)</li>
<li>chore: update known checksums for 0.13.2/0.13.3 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1098</a>)</li>
<li>chore: update known checksums for 0.13.1 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1094</a>)</li>
<li>Verify npm dependency signatures before builds <a href="https://github.com/zaniebot"><code>@​zaniebot</code></a> (<a href="">#1027</a>)</li>
</ul>
<h2>📚 Documentation</h2>
<ul>
<li>docs: cache-dependency-glob matches relative to the working directory <a href="https://github.com/flange-ipb"><code>@​flange-ipb</code></a> (<a href="">#1092</a>)</li>
<li>docs: update version references to v10.3.0 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1090</a>)</li>
</ul>
<h2>⬆️ Dependency updates</h2>
<ul>
<li>chore(deps): roll up Dependabot updates <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#1101</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>18d369b</code></a> chore(deps): roll up Dependabot updates (<a href="">#1101</a>)</li>
<li><a href=""><code>4ad2329</code></a> chore: update known checksums for 0.13.4 (<a href="">#1099</a>)</li>
<li><a href=""><code>4bc6759</code></a> chore: update known checksums for 0.13.2/0.13.3 (<a href="">#1098</a>)</li>
<li><a href=""><code>c97f06e</code></a> fix: preserve cache error class names in save-cache bundle (<a href="">#1093</a>)</li>
<li><a href=""><code>8ca4be0</code></a> chore: update known checksums for 0.13.1 (<a href="">#1094</a>)</li>
<li><a href=""><code>b627d85</code></a> docs: cache-dependency-glob matches relative to the working directory (<a href="">#1092</a>)</li>
<li><a href=""><code>f8c8897</code></a> Verify npm dependency signatures before builds (<a href="">#1027</a>)</li>
<li><a href=""><code>f64d32b</code></a> docs: update version references to v10.3.0 (<a href="">#1090</a>)</li>
<li>See full diff in <a href="https://github.com/astral-sh/setup-uv/compare/1c37ad07a6a961277cf70c0d37d6f313000f5884...18d369b23da25a81e9458561248e1aafff6a70fa">compare view</a></li>
</ul>
</details>
<br />

Updates `pypa/gh-action-pypi-publish` from 1.14.2 to 1.14.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/gh-action-pypi-publish/releases">pypa/gh-action-pypi-publish's releases</a>.</em></p>
<blockquote>
<h2>v1.14.3</h2>
<!-- raw HTML omitted -->
<blockquote>
<p>[!important]
🚨 This release includes fixes for <a href="https://github.com/pypa/gh-action-pypi-publish/security/advisories/GHSA-5xjx-3w67-w9x9">GHSA-5xjx-3w67-w9x9</a> patched up by <a href="https://github.com/sethmlarson"><code>@​sethmlarson</code></a><a href="https://github.com/sponsors/sethmlarson">💰</a> in <a href="">#427</a> and in other places across the ecosystem.</p>
<p>Additional ecosystem and related mitigations beyond you might want to watch out for:</p>
<ul>
<li><a href="https://discuss.python.org/t/information-for-python-users-regarding-emudhra-emsign-ca-certificate-security-incident/109576">https://discuss.python.org/t/information-for-python-users-regarding-emudhra-emsign-ca-certificate-security-incident/109576</a></li>
<li><a href="https://emudhra.we-have-a-problem.com">https://emudhra.we-have-a-problem.com</a></li>
</ul>
</blockquote>
<h2>🛠️ Security Tightening</h2>
<p><a href="https://github.com/webknjaz"><code>@​webknjaz</code></a><a href="https://github.com/sponsors/webknjaz">💰</a> made sure the dependency tree within the action runtime uses hash-checking from now on via <a href="">pypa/gh-action-pypi-publish#420</a>.</p>
<p><strong>🪞 Full Diff</strong>: <a href="https://github.com/pypa/gh-action-pypi-publish/compare/v1.14.2...v1.14.3">https://github.com/pypa/gh-action-pypi-publish/compare/v1.14.2...v1.14.3</a></p>
<p><strong>🧔‍♂️ Release Manager:</strong> <a href="https://github.com/sponsors/webknjaz"><code>@​webknjaz</code></a> <a href="https://stand-with-ukraine.pp.ua">🇺🇦</a></p>
<p><strong>💬 Discuss</strong> <a href="https://bsky.app/profile/webknjaz.me/post/3mydcjweyak2f">on Bluesky 🦋</a>, <a href="https://mastodon.social/@webknjaz/117474743338290807">on Mastodon 🐘</a> and <a href="https://github.com/pypa/gh-action-pypi-publish/discussions/429">on GitHub</a>.</p>
<p><a href="https://github.com/sponsors/webknjaz"><img src="https://img.shields.io/badge/%40webknjaz-transparent?logo=githubsponsors&amp;logoColor=%23EA4AAA&amp;label=Sponsor&amp;color=2a313c" alt="GH Sponsors badge" /></a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7245906</code></a> Merge pull request <a href="">#427</a> from sethmlarson/certifi-sigstore</li>
<li><a href=""><code>331eccb</code></a> Upgrade certifi and sigstore</li>
<li><a href=""><code>f68fee4</code></a> 💰 Sync the FUNDING config</li>
<li><a href=""><code>c0d6f8e</code></a> Merge branch 'integrity/runtime/deptree' into unstable/v1</li>
<li><a href=""><code>9090099</code></a> 🧪 Make smoke test deps hash-pinned in CI</li>
<li><a href=""><code>34e40c2</code></a> 📌 Bump pip-tools managed transitive deptrees</li>
<li><a href=""><code>e800ed5</code></a> 👷 Enable hash-checking in the runtime deptree 🔗</li>
<li><a href=""><code>dd8c5f4</code></a> 🔧 Make pip-tools config available in container</li>
<li>See full diff in <a href="https://github.com/pypa/gh-action-pypi-publish/compare/dc37677b2e1c63e2034f94d8a5b11f265b73ba33...7245906fb61fa33a13554f9d5fb856fe61758086">compare view</a></li>
</ul>
</details>
<br />

Updates `actions/setup-python` from 7.0.0 to 7.1.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/setup-python/releases">actions/setup-python's releases</a>.</em></p>
<blockquote>
<h2>v7.1.0</h2>
<h2>What's Changed</h2>
<h3>Enhancements</h3>
<ul>
<li>Add <code>mirror</code> and <code>mirror-token</code> inputs for custom Python distribution sources by <a href="https://github.com/luhenry"><code>@​luhenry</code></a> in <a href="">actions/setup-python#1302</a></li>
<li>Improve error message clarity by <a href="https://github.com/v-lmvysakh"><code>@​v-lmvysakh</code></a> in <a href="">actions/setup-python#1351</a></li>
</ul>
<h3>Dependency Upgrade</h3>
<ul>
<li>Upgrade browserslist from 4.28.2 to 4.28.9 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1353</a></li>
<li>Upgrade <code>@​typescript-eslint/parser</code> from 8.62.0 to 8.70.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1343</a></li>
<li>Upgrade eslint-plugin-jest from 29.15.2 to 29.16.6 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1342</a></li>
<li>Upgrade <code>@​vercel/ncc</code> from 0.44.0 to 0.45.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1357</a></li>
<li>Upgrade <code>@​types/semver</code> from 7.7.1 to 7.8.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1359</a></li>
<li>Upgrade undici from 6.28.0 to 6.29.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1364</a></li>
<li>Upgrade ts-jest from 29.4.11 to 29.4.14 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1361</a></li>
<li>Upgrade brace-expansion from 5.0.9 to 5.0.12 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1365</a></li>
<li>Upgrade prettier from 3.8.4 to 3.9.9 and package.json from 7.0.0 to 7.1.0 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1363</a></li>
<li>Upgrade <code>@​typescript-eslint/eslint-plugin</code> from 8.62.0 to 8.71.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1369</a></li>
<li>Upgrade actions/checkout from 7.0.0 to 7.0.1 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1345</a></li>
<li>Upgrade cache to 6.3.0 by <a href="https://github.com/v-HarithaVattikuti"><code>@​v-HarithaVattikuti</code></a> in <a href="">actions/setup-python#1370</a></li>
<li>Resolve Basic Validation audit failures by <a href="https://github.com/v-HarithaVattikuti"><code>@​v-HarithaVattikuti</code></a> in <a href="">actions/setup-python#1347</a></li>
<li>Resolve npm audit failures by <a href="https://github.com/v-HarithaVattikuti"><code>@​v-HarithaVattikuti</code></a> in <a href="">actions/setup-python#1350</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/luhenry"><code>@​luhenry</code></a> made their first contribution in <a href="">actions/setup-python#1302</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/setup-python/compare/v7.0.0...v7.1.0">https://github.com/actions/setup-python/compare/v7.0.0...v7.1.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6d4fd22</code></a> Cache upgrade to 6.3.0 (<a href="">#1370</a>)</li>
<li><a href=""><code>ec52d0a</code></a> Bump <code>@​typescript-eslint/eslint-plugin</code> from 8.62.0 to 8.71.1 (<a href="">#1369</a>)</li>
<li><a href=""><code>ff73b24</code></a> Bump prettier from 3.8.4 to 3.9.9 and package.json from 7.0.0 to 7.1.0 (<a href="">#1363</a>)</li>
<li><a href=""><code>0e40890</code></a> Bump brace-expansion from 5.0.9 to 5.0.12 (<a href="">#1365</a>)</li>
<li><a href=""><code>3892123</code></a> Bump ts-jest from 29.4.11 to 29.4.14 (<a href="">#1361</a>)</li>
<li><a href=""><code>6609657</code></a> Bump undici from 6.28.0 to 6.29.0 (<a href="">#1364</a>)</li>
<li><a href=""><code>e1be392</code></a> Bump <code>@​types/semver</code> from 7.7.1 to 7.8.0 (<a href="">#1359</a>)</li>
<li><a href=""><code>06da627</code></a> Bump <code>@​vercel/ncc</code> from 0.44.0 to 0.45.0 (<a href="">#1357</a>)</li>
<li><a href=""><code>af9bcc7</code></a> Bump eslint-plugin-jest from 29.15.2 to 29.16.6 (<a href="">#1342</a>)</li>
<li><a href=""><code>7aeabeb</code></a> Bump <code>@​typescript-eslint/parser</code> from 8.62.0 to 8.70.0 (<a href="">#1343</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/actions/setup-python/compare/5fda3b95a4ea91299a34e894583c3862153e4b97...6d4fd22b20465ccc0f7354476588e8df7c9ca0e0">compare view</a></li>
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