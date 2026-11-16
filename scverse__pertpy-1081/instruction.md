# Issue

**Title:** Bump astral-sh/setup-uv from 9.0.0 to 10.0.0 in the actions-deps group

## Description

Bumps the actions-deps group with 1 update: [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv).

Updates `astral-sh/setup-uv` from 9.0.0 to 10.0.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/setup-uv/releases">astral-sh/setup-uv's releases</a>.</em></p>
<blockquote>
<h2>v10.0.0 🌈 Disable automatic caching for sensitive events and new QOL features</h2>
<h2>Changes</h2>
<p>Another breaking release, directly after v9.0.0 but we think the added security justifies that.</p>
<h3>Extra security by default</h3>
<p>If you use the default <code>enable-cache: auto</code> this will now <strong>DISABLE THE CACHE</strong> to protect against cache poisoning for the following events:</p>
<ul>
<li><code>pull_request_target</code></li>
<li><code>workflow_run</code></li>
<li><code>release</code></li>
</ul>
<p>You can read the full reasoning in <a href="">astral-sh/setup-uv#984</a></p>
<h3><code>version: latest-known</code></h3>
<pre lang="yaml"><code>- name: Install the latest version of uv known to setup-uv
  uses: astral-sh/setup-uv@v10.0.0
  with:
    version: &quot;latest-known&quot;
</code></pre>
<p>This will now install the latest version with a checksum that is known by this action. The <a href="https://github.com/astral-sh/setup-uv/blob/4f6036f71cec78afb113b323f220c9185d983c12/src/download/checksum/known-checksums.ts">known <code>uv</code> checksums</a> are automatically updated but will take a release of this action to take effect. You won't be always using the latest &amp; greatest but you will have an extra level of security.</p>
<h3>Read python version from <code>.tool-versions</code></h3>
<pre lang="yaml"><code>- name: Install uv based on the version defined in .tool-versions and also set python
  uses: astral-sh/setup-uv@v10.0.0
  with:
    version-file: &quot;pyproject.toml&quot;
</code></pre>
<p>Will now also set the python version if it is defined in <code>.tool-versions</code>. You can read the details <a href="https://github.com/astral-sh/setup-uv/blob/main/docs/advanced-version-configuration.md#install-a-version-defined-in-a-requirements-or-config-file">in the docs</a></p>
<h2>🚨 Breaking changes</h2>
<ul>
<li>Disable automatic caching for sensitive events <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#992</a>)</li>
</ul>
<h2>🐛 Bug fixes</h2>
<ul>
<li>Reject paths in .tool-versions <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#1007</a>)</li>
</ul>
<h2>🚀 Enhancements</h2>
<ul>
<li>Read Python version from .tool-versions <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#996</a>)</li>
<li>Add latest-known version selector <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#993</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ae62891</code></a> chore(deps): roll up Dependabot updates (<a href="">#1013</a>)</li>
<li><a href=""><code>f9cdb47</code></a> Reject paths in .tool-versions (<a href="">#1007</a>)</li>
<li><a href=""><code>4f6036f</code></a> Require pull requests for Dependabot rollups (<a href="">#1005</a>)</li>
<li><a href=""><code>8d6402c</code></a> chore(deps): roll up Dependabot updates (<a href="">#1004</a>)</li>
<li><a href=""><code>46f427b</code></a> Read Python version from .tool-versions (<a href="">#996</a>)</li>
<li><a href=""><code>8ed89c5</code></a> ci: pin Alpine container image (<a href="">#995</a>)</li>
<li><a href=""><code>8473c7f</code></a> chore(deps): roll up Dependabot updates (<a href="">#994</a>)</li>
<li><a href=""><code>18d451d</code></a> Add latest-known version selector (<a href="">#993</a>)</li>
<li><a href=""><code>f451684</code></a> Disable automatic caching for sensitive events (<a href="">#992</a>)</li>
<li><a href=""><code>b68407c</code></a> chore: update known checksums for 0.12.3 (<a href="">#991</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/astral-sh/setup-uv/compare/c771a70e6277c0a99b617c7a806ffedaca235ff9...ae62891fec2bb8e7d6c99fc78c9fec3a63790f8d">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=astral-sh/setup-uv&package-manager=github_actions&previous-version=9.0.0&new-version=10.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2831c5b2a4a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.