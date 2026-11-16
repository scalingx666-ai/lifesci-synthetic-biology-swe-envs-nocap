# Issue

**Title:** Bump the actions-deps group with 3 updates

## Description

Bumps the actions-deps group with 3 updates: [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv), [r-lib/actions/setup-r](https://github.com/r-lib/actions) and [r-lib/actions/setup-r-dependencies](https://github.com/r-lib/actions).

Updates `astral-sh/setup-uv` from 10.1.0 to 10.2.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/setup-uv/releases">astral-sh/setup-uv's releases</a>.</em></p>
<blockquote>
<h2>v10.2.0 🌈 Disable automatic cache saves for merge queues</h2>
<h2>Changes</h2>
<p>This release contains the known-checksum of the most recent uv releases and also disabled the uploading(saving) of the cache when in a merge queue since theses caches would almost never be used.</p>
<h2>🚀 Enhancements</h2>
<ul>
<li>Disable automatic cache saves for merge queues <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#1056</a>)</li>
</ul>
<h2>🧰 Maintenance</h2>
<ul>
<li>chore: update known checksums for 0.12.17 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1058</a>)</li>
<li>chore: update known checksums for 0.12.16 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1057</a>)</li>
<li>chore: update known checksums for 0.12.15 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1054</a>)</li>
<li>chore: update known checksums for 0.12.14 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1053</a>)</li>
<li>chore: update known checksums for 0.12.13 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1045</a>)</li>
</ul>
<h2>📚 Documentation</h2>
<ul>
<li>docs: update version references to v10.1.0 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#1044</a>)</li>
</ul>
<h2>⬆️ Dependency updates</h2>
<ul>
<li>chore(deps): roll up Dependabot updates <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#1059</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c18668a</code></a> chore(deps): roll up Dependabot updates (<a href="">#1059</a>)</li>
<li><a href=""><code>ffe1476</code></a> chore: update known checksums for 0.12.17 (<a href="">#1058</a>)</li>
<li><a href=""><code>f5548c5</code></a> chore: update known checksums for 0.12.16 (<a href="">#1057</a>)</li>
<li><a href=""><code>a761a4e</code></a> Disable automatic cache saves for merge queues (<a href="">#1056</a>)</li>
<li><a href=""><code>3377a30</code></a> chore: update known checksums for 0.12.15 (<a href="">#1054</a>)</li>
<li><a href=""><code>dfb5f38</code></a> chore: update known checksums for 0.12.14 (<a href="">#1053</a>)</li>
<li><a href=""><code>45c121f</code></a> chore: update known checksums for 0.12.13 (<a href="">#1045</a>)</li>
<li><a href=""><code>8073452</code></a> docs: update version references to v10.1.0 (<a href="">#1044</a>)</li>
<li>See full diff in <a href="https://github.com/astral-sh/setup-uv/compare/bec219d24cd3e171d82865faccec33120bb574f4...c18668ad3cf93ea998bef934396af7bb5c839dc7">compare view</a></li>
</ul>
</details>
<br />

Updates `r-lib/actions/setup-r` from 2.13.0 to 2.14.0
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/r-lib/actions/blob/v2-branch/NEWS.md">r-lib/actions/setup-r's changelog</a>.</em></p>
<blockquote>
<h1>'v2.14.0` (2026-09-21)</h1>
<ul>
<li>
<p><code>[setup-r]</code>: <code>use-public-rspm: true</code> now sets up P3M (<a href="https://p3m.dev">https://p3m.dev</a>)
on macOS as well, for all repositories.</p>
</li>
<li>
<p><code>[setup-r]</code> now installs flang 23 on R 4.7.0 (current R-devel) and
later, as this is what CRAN uses now (<a href="">#1107</a>, <a href="https://github.com/andrjohns"><code>@​andrjohns</code></a>).</p>
</li>
<li>
<p><code>[check-r-package]</code> now uses the correct check directory when showing
the testthat output (<a href="">#1109</a>, <a href="https://github.com/NotAFlightRisk"><code>@​NotAFlightRisk</code></a>).</p>
</li>
</ul>
<h1><code>v2.13.0</code> (2026-08-28)</h1>
<ul>
<li>
<p><code>[setup-r]</code> now retries r-hub.io HTTP failures (<a href="">#1088</a>, <a href="https://github.com/nbenn"><code>@​nbenn</code></a>).</p>
</li>
<li>
<p><code>[setup-r]</code> now sets the correct RTOOLS environment variables on
aarch64 Windows (<a href="https://github.com/vjymisal0"><code>@​vjymisal0</code></a>, <a href="">#1104</a>).</p>
</li>
<li>
<p><code>[setup-r]</code> keep repositories if they are set by the build.
E.g. aarch64 Windows builds now set them (<a href="https://github.com/jeroen"><code>@​jeroen</code></a>, <a href="">#1101</a>).</p>
</li>
<li>
<p><code>[setup-r]</code> now retries transient failures when resolving the R
version from <code>api.r-hub.io</code>, rather than failing the job on the first
timeout or server error (<a href="https://github.com/nbenn"><code>@​nbenn</code></a>, <a href="">#1086</a>).</p>
</li>
<li>
<p><code>[setup-r-dependencies]</code> now switches back to classic <code>sudo</code>, if
available, on Linux. This fixes installing pak on Ubuntu 26.04 runners
(<a href="https://github.com/jeroen"><code>@​jeroen</code></a>, <a href="">#1096</a>).</p>
</li>
</ul>
<h1><code>v2.12.1</code> (2026-06-23)</h1>
<ul>
<li>
<p><code>[setup-r]</code> now avoids a warning about an <code>url.parse()</code> deprecation
(<a href="">#1074</a>).</p>
</li>
<li>
<p><code>[setup-r-dependencies]</code> now uses <code>quarto-dev/quarto-actions</code> <code>v2.2.0</code>
(<a href="https://github.com/jdblischak"><code>@​jdblischak</code></a>, <a href="">#1076</a>).</p>
</li>
<li>
<p>Examples: <code>test-coverage.yaml</code> now uses <code>codecov/codecov-action</code> <code>v7</code>
(<a href="https://github.com/shikokuchuo"><code>@​shikokuchuo</code></a>, <a href="">#1081</a>).</p>
</li>
<li>
<p>New example <code>claude-investigate.yaml</code> workflow (<a href="https://github.com/DavisVaughan"><code>@​DavisVaughan</code></a>, <a href="">#1084</a>).</p>
</li>
</ul>
<h1><code>v2.12.0</code> (2026-04-29)</h1>
<ul>
<li>
<p>All node.js actions use node 24 now. Relatedly, all example workflows
use recent versions of actions that use node 24.</p>
</li>
<li>
<p><code>[setup-r]</code> now uses <code>use-public-rspm: true</code> by default on Linux and
Windows. macOS binaries require further opt-in with
<code>use-public-rspm: always</code>.</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f9a764f</code></a> Update NEWS before release (<a href="">#1111</a>)</li>
<li><a href=""><code>3a1a90f</code></a> [setup-r] <code>use-public-rspm: true</code> is TRUE for all repos on macOS (<a href="">#1110</a>)</li>
<li><a href=""><code>0e37acd</code></a> setup-r: Add installation for flang on mac r-devel (<a href="">#1108</a>)</li>
<li><a href=""><code>196dc04</code></a> [check-r-package] Use the resolved check-dir when showing testthat output (<a href="">#1</a>...</li>
<li><a href=""><code>8efa420</code></a> Fix typo (<a href="">#1106</a>)</li>
<li>See full diff in <a href="https://github.com/r-lib/actions/compare/465b7d8e732ca3921382b1674c59bada9cbf3399...f9a764fea8d5c63df6ef9a5c7795bf7deb5d7e05">compare view</a></li>
</ul>
</details>
<br />

Updates `r-lib/actions/setup-r-dependencies` from 2.13.0 to 2.14.0
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/r-lib/actions/blob/v2-branch/NEWS.md">r-lib/actions/setup-r-dependencies's changelog</a>.</em></p>
<blockquote>
<h1>'v2.14.0` (2026-09-21)</h1>
<ul>
<li>
<p><code>[setup-r]</code>: <code>use-public-rspm: true</code> now sets up P3M (<a href="https://p3m.dev">https://p3m.dev</a>)
on macOS as well, for all repositories.</p>
</li>
<li>
<p><code>[setup-r]</code> now installs flang 23 on R 4.7.0 (current R-devel) and
later, as this is what CRAN uses now (<a href="">#1107</a>, <a href="https://github.com/andrjohns"><code>@​andrjohns</code></a>).</p>
</li>
<li>
<p><code>[check-r-package]</code> now uses the correct check directory when showing
the testthat output (<a href="">#1109</a>, <a href="https://github.com/NotAFlightRisk"><code>@​NotAFlightRisk</code></a>).</p>
</li>
</ul>
<h1><code>v2.13.0</code> (2026-08-28)</h1>
<ul>
<li>
<p><code>[setup-r]</code> now retries r-hub.io HTTP failures (<a href="">#1088</a>, <a href="https://github.com/nbenn"><code>@​nbenn</code></a>).</p>
</li>
<li>
<p><code>[setup-r]</code> now sets the correct RTOOLS environment variables on
aarch64 Windows (<a href="https://github.com/vjymisal0"><code>@​vjymisal0</code></a>, <a href="">#1104</a>).</p>
</li>
<li>
<p><code>[setup-r]</code> keep repositories if they are set by the build.
E.g. aarch64 Windows builds now set them (<a href="https://github.com/jeroen"><code>@​jeroen</code></a>, <a href="">#1101</a>).</p>
</li>
<li>
<p><code>[setup-r]</code> now retries transient failures when resolving the R
version from <code>api.r-hub.io</code>, rather than failing the job on the first
timeout or server error (<a href="https://github.com/nbenn"><code>@​nbenn</code></a>, <a href="">#1086</a>).</p>
</li>
<li>
<p><code>[setup-r-dependencies]</code> now switches back to classic <code>sudo</code>, if
available, on Linux. This fixes installing pak on Ubuntu 26.04 runners
(<a href="https://github.com/jeroen"><code>@​jeroen</code></a>, <a href="">#1096</a>).</p>
</li>
</ul>
<h1><code>v2.12.1</code> (2026-06-23)</h1>
<ul>
<li>
<p><code>[setup-r]</code> now avoids a warning about an <code>url.parse()</code> deprecation
(<a href="">#1074</a>).</p>
</li>
<li>
<p><code>[setup-r-dependencies]</code> now uses <code>quarto-dev/quarto-actions</code> <code>v2.2.0</code>
(<a href="https://github.com/jdblischak"><code>@​jdblischak</code></a>, <a href="">#1076</a>).</p>
</li>
<li>
<p>Examples: <code>test-coverage.yaml</code> now uses <code>codecov/codecov-action</code> <code>v7</code>
(<a href="https://github.com/shikokuchuo"><code>@​shikokuchuo</code></a>, <a href="">#1081</a>).</p>
</li>
<li>
<p>New example <code>claude-investigate.yaml</code> workflow (<a href="https://github.com/DavisVaughan"><code>@​DavisVaughan</code></a>, <a href="">#1084</a>).</p>
</li>
</ul>
<h1><code>v2.12.0</code> (2026-04-29)</h1>
<ul>
<li>
<p>All node.js actions use node 24 now. Relatedly, all example workflows
use recent versions of actions that use node 24.</p>
</li>
<li>
<p><code>[setup-r]</code> now uses <code>use-public-rspm: true</code> by default on Linux and
Windows. macOS binaries require further opt-in with
<code>use-public-rspm: always</code>.</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f9a764f</code></a> Update NEWS before release (<a href="">#1111</a>)</li>
<li><a href=""><code>3a1a90f</code></a> [setup-r] <code>use-public-rspm: true</code> is TRUE for all repos on macOS (<a href="">#1110</a>)</li>
<li><a href=""><code>0e37acd</code></a> setup-r: Add installation for flang on mac r-devel (<a href="">#1108</a>)</li>
<li><a href=""><code>196dc04</code></a> [check-r-package] Use the resolved check-dir when showing testthat output (<a href="">#1</a>...</li>
<li><a href=""><code>8efa420</code></a> Fix typo (<a href="">#1106</a>)</li>
<li>See full diff in <a href="https://github.com/r-lib/actions/compare/465b7d8e732ca3921382b1674c59bada9cbf3399...f9a764fea8d5c63df6ef9a5c7795bf7deb5d7e05">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `199ba30b274d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.