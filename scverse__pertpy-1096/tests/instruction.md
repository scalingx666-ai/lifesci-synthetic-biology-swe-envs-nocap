# Issue

**Title:** Bump the actions-deps group with 2 updates

## Description

Bumps the actions-deps group with 2 updates: [r-lib/actions/setup-r](https://github.com/r-lib/actions) and [r-lib/actions/setup-r-dependencies](https://github.com/r-lib/actions).

Updates `r-lib/actions/setup-r` from 2.12.1 to 2.13.0
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/r-lib/actions/blob/v2-branch/NEWS.md">r-lib/actions/setup-r's changelog</a>.</em></p>
<blockquote>
<h1><code>v2.13.0</code> (2026-08028)</h1>
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
<li>
<p>It is now possible to require actions to be pinned to a full-length
commit SHA in repositories using <code>r-lib/actions</code> (<a href="">#1070</a>).</p>
</li>
<li>
<p><code>[setup-pandoc][setup-r-dependencies]</code> now default to Pandoc
version 3.8.3.</p>
</li>
<li>
<p><code>[setup-r-dependencies]</code> now includes the R architecture in the
cache key, so caches for <code>macos-15</code> (Apple Silicon) and
<code>macos-15-intel</code> (Rosetta/x86_64) no longer collide (<a href="">#1035</a>).</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>465b7d8</code></a> NEWS for 2.13.0 (<a href="">#1105</a>)</li>
<li><a href=""><code>d06a540</code></a> [setup-r] retry transient r-hub.io request failures (<a href="">#1088</a>)</li>
<li><a href=""><code>ed9aa85</code></a> fix(setup-r): export correct RTOOLS HOME env vars on Windows ARM64 and x64 (#...</li>
<li><a href=""><code>c86f32c</code></a> setup-r-dependencies: set JAVA_HOME on Windows runners from Java 21 env vars ...</li>
<li><a href=""><code>2a66450</code></a> setup-r-dependencies: switch back to classic sudo on runners with sudo-rs (<a href="">#1</a>...</li>
<li><a href=""><code>5cc1f0d</code></a> Fix minor typo (<a href="">#1098</a>)</li>
<li><a href=""><code>33d09fb</code></a> fix: Remove stray <code>::group::</code> (<a href="">#1103</a>)</li>
<li><a href=""><code>aae88a2</code></a> Special-case CRAN mirror for Windows ARM64 (<a href="">#1101</a>)</li>
<li><a href=""><code>b7484da</code></a> [setup-r] Support installing RTools without installing R (<a href="">#1093</a>)</li>
<li>See full diff in <a href="https://github.com/r-lib/actions/compare/d3c5be51b12e724e68f33216ca3c148b66d5f0b6...465b7d8e732ca3921382b1674c59bada9cbf3399">compare view</a></li>
</ul>
</details>
<br />

Updates `r-lib/actions/setup-r-dependencies` from 2.12.1 to 2.13.0
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/r-lib/actions/blob/v2-branch/NEWS.md">r-lib/actions/setup-r-dependencies's changelog</a>.</em></p>
<blockquote>
<h1><code>v2.13.0</code> (2026-08028)</h1>
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
<li>
<p>It is now possible to require actions to be pinned to a full-length
commit SHA in repositories using <code>r-lib/actions</code> (<a href="">#1070</a>).</p>
</li>
<li>
<p><code>[setup-pandoc][setup-r-dependencies]</code> now default to Pandoc
version 3.8.3.</p>
</li>
<li>
<p><code>[setup-r-dependencies]</code> now includes the R architecture in the
cache key, so caches for <code>macos-15</code> (Apple Silicon) and
<code>macos-15-intel</code> (Rosetta/x86_64) no longer collide (<a href="">#1035</a>).</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>465b7d8</code></a> NEWS for 2.13.0 (<a href="">#1105</a>)</li>
<li><a href=""><code>d06a540</code></a> [setup-r] retry transient r-hub.io request failures (<a href="">#1088</a>)</li>
<li><a href=""><code>ed9aa85</code></a> fix(setup-r): export correct RTOOLS HOME env vars on Windows ARM64 and x64 (#...</li>
<li><a href=""><code>c86f32c</code></a> setup-r-dependencies: set JAVA_HOME on Windows runners from Java 21 env vars ...</li>
<li><a href=""><code>2a66450</code></a> setup-r-dependencies: switch back to classic sudo on runners with sudo-rs (<a href="">#1</a>...</li>
<li><a href=""><code>5cc1f0d</code></a> Fix minor typo (<a href="">#1098</a>)</li>
<li><a href=""><code>33d09fb</code></a> fix: Remove stray <code>::group::</code> (<a href="">#1103</a>)</li>
<li><a href=""><code>aae88a2</code></a> Special-case CRAN mirror for Windows ARM64 (<a href="">#1101</a>)</li>
<li><a href=""><code>b7484da</code></a> [setup-r] Support installing RTools without installing R (<a href="">#1093</a>)</li>
<li>See full diff in <a href="https://github.com/r-lib/actions/compare/d3c5be51b12e724e68f33216ca3c148b66d5f0b6...465b7d8e732ca3921382b1674c59bada9cbf3399">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3001be83e49b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.