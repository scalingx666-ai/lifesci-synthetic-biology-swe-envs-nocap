# Issue

**Title:** Bump the actions-deps group with 2 updates

## Description

Bumps the actions-deps group with 2 updates: [pypa/gh-action-pypi-publish](https://github.com/pypa/gh-action-pypi-publish) and [release-drafter/release-drafter](https://github.com/release-drafter/release-drafter).

Updates `pypa/gh-action-pypi-publish` from 1.14.1 to 1.14.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/gh-action-pypi-publish/releases">pypa/gh-action-pypi-publish's releases</a>.</em></p>
<blockquote>
<h2>v1.14.2</h2>
<!-- raw HTML omitted -->
<h2>🛠️ Urgh… Another release!? Again? Explain yourself!</h2>
<p>Looking at the diff, you'll only witness updates across the dependency tree. That's it! It's not a security fix or anything like that even, no. But you'll want this update.</p>
<blockquote>
<p>[!tip]
So what <em>most</em> people will find useful is <a href="https://github.com/takluyver"><code>@​takluyver</code></a><a href="https://github.com/sponsors/takluyver">💰</a>'s update of Twine to v7 that we use internally (<a href="">#416</a>). This version will let them upload their sdists and wheels containing core packaging metadata v2.5 to (Test)PyPI.</p>
</blockquote>
<h2>🧐 Tell me why..</h2>
<!-- raw HTML omitted -->
<!-- raw HTML omitted -->
<p>TL;DR non-pure-python projects with C-extensions tend to have dozens (sometimes hundreds) wheels to upload to PyPI per release. They are often quite big and take time to transfer over the network. People started noticing problems and coming up with DIY sharding workarounds like <a href="">aio-libs/aiohttp#13226</a> around July 23.
On this date, projects with a good amount of bytes to publish would start getting timeouts 5 minutes after the PyPI publishing job begun. The same job that worked just fine before.</p>
<p>I had to start pinging upstream library and ecosystem people, on GitHub and privately, to start making sense of what was happening. Eventually, we collectively concluded that GitHub must've shortened the lifetime of their OIDC identity — it seems to have used to be 10 minutes long (at some point in the past) and is now 5 minutes, apparently. It's not documented clearly, and we have not been able to get any clarity by attempting to contact GitHub through private channels, using personal connections.</p>
<p>Over the course of investigation, <a href="https://github.com/facutuesca"><code>@​facutuesca</code></a><a href="https://github.com/sponsors/facutuesca">💰</a> found and fixed a related underlying cache invalidation bug in <a href="">sigstore/sigstore-python#1838</a>, which he then coordinated propagation through the dependency chain updates in sigstore-python, pypi-attestations, gh-action-pypi-publish and gh-action-sigstore-python.</p>
<p>Mike's also discovered that Sigstore's Rekor slowdown seems to have become the main contributing cause of the last week's incident. He's collected some data to support this claim: <a href="https://publishing-five-minute-timeout.tiiny.site">https://publishing-five-minute-timeout.tiiny.site</a>.</p>
<!-- raw HTML omitted -->
<!-- raw HTML omitted -->
<h2>🫶 New Contributors</h2>
<ul>
<li><a href="https://github.com/davidbrochart"><code>@​davidbrochart</code></a> made their first contribution in <a href="">#415</a></li>
<li><a href="https://github.com/takluyver"><code>@​takluyver</code></a> made their first contribution in <a href="">#416</a></li>
</ul>
<p><strong>🪞 Full Diff</strong>: <a href="https://github.com/pypa/gh-action-pypi-publish/compare/v1.14.1...v1.14.2">https://github.com/pypa/gh-action-pypi-publish/compare/v1.14.1...v1.14.2</a></p>
<p><strong>🧔‍♂️ Release Manager:</strong> <a href="https://github.com/sponsors/webknjaz"><code>@​webknjaz</code></a> <a href="https://stand-with-ukraine.pp.ua">🇺🇦</a></p>
<p><strong>🙏 Special Thanks</strong> to <a href="https://github.com/davidbrochart"><code>@​davidbrochart</code></a><a href="https://github.com/sponsors/davidbrochart">💰</a> and <a href="https://github.com/Dreamsorcerer"><code>@​Dreamsorcerer</code></a><a href="https://github.com/sponsors/Dreamsorcerer">💰</a> for turning my attention (in <a href="">#415</a> and in private) to the newly surfaced corner case in GitHub's behavior that only affected a narrow category of projects while many others remained blissfully unaware. <a href="https://github.com/bdraco"><code>@​bdraco</code></a><a href="https://github.com/sponsors/bdraco">💰</a> came up with a DIY sharding workaround for aiohttp that served as a demo for other projects. <a href="https://github.com/miketheman"><code>@​miketheman</code></a><a href="https://github.com/sponsors/miketheman">💰</a> confirmed the Warehouse-side details. Also, <a href="https://github.com/jku"><code>@​jku</code></a><a href="https://github.com/sponsors/jku">💰</a> and <a href="https://github.com/woodruffw"><code>@​woodruffw</code></a><a href="https://github.com/sponsors/woodruffw">💰</a> helped work through, review and release the Sigstore ecosystem upstream libs.</p>
<p><strong>💬 Discuss</strong> <a href="https://bsky.app/profile/did:plc:ve6s3mxkefjaxty3m4fdqumn/post/3mrsqy2xba22j">on Bluesky 🦋</a>, <a href="https://mastodon.social/@webknjaz/117005132816750073">on Mastodon 🐘</a> and [on GitHub][release discussion].</p>
<p>[![GH Sponsors badge]][GH Sponsors URL]</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>dc37677</code></a> Merge pull request <a href="">#417</a> from trail-of-forks/ft/bump-deps</li>
<li><a href=""><code>8b2f234</code></a> Bump <code>pypi-attestations</code> and <code>sigstore</code></li>
<li><a href=""><code>78b72db</code></a> Merge pull request <a href="">#416</a> from takluyver/twine-v7</li>
<li><a href=""><code>92f4d2a</code></a> Update twine to v7</li>
<li>See full diff in <a href="https://github.com/pypa/gh-action-pypi-publish/compare/ba38be9e461d3875417946c167d0b5f3d385a247...dc37677b2e1c63e2034f94d8a5b11f265b73ba33">compare view</a></li>
</ul>
</details>
<br />

Updates `release-drafter/release-drafter` from 7.6.0 to 7.7.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/release-drafter/release-drafter/releases">release-drafter/release-drafter's releases</a>.</em></p>
<blockquote>
<h2>v7.7.0</h2>
<h1>What's Changed</h1>
<h2>New</h2>
<ul>
<li>feat: no new contributor template (<a href="">#1687</a>) <a href="https://github.com/cchanche"><code>@​cchanche</code></a></li>
<li>feat: categorize PRs based on conventional title (<a href="">#1556</a>) <a href="https://github.com/cchanche"><code>@​cchanche</code></a></li>
<li>feat: log all config sources (<a href="">#1674</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<h2>Dependency Updates</h2>
<!-- raw HTML omitted -->
<ul>
<li>build(deps-dev): bump postcss from 8.5.17 to 8.5.23 (<a href="">#1683</a>) <a href="https://github.com/apps/dependabot"><code>@​dependabot[bot]</code></a></li>
<li>chore(deps): update npm tool constraint to 12.0.1 (<a href="">#1668</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a>, <a href="https://github.com/cchanche"><code>@​cchanche</code></a></li>
<li>chore(deps): update npm tool constraint to 11.18.0 (<a href="">#1665</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a>, <a href="https://github.com/cchanche"><code>@​cchanche</code></a></li>
<li>chore(deps): update node.js to v24.18.0 (<a href="">#1664</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>build(deps): support GraphQL 17 (<a href="">#1678</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>build(deps-dev): Update js-yaml to 4.3.0 (<a href="">#1677</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>build(deps-dev): bump shell-quote from 1.8.4 to 1.10.0 (<a href="">#1676</a>) <a href="https://github.com/apps/dependabot"><code>@​dependabot[bot]</code></a></li>
<li>build(deps): bump immutable from 5.1.5 to 5.1.9 (<a href="">#1675</a>) <a href="https://github.com/apps/dependabot"><code>@​dependabot[bot]</code></a></li>
<li>build(deps-dev): bump brace-expansion from 5.0.6 to 5.0.7 (<a href="">#1672</a>) <a href="https://github.com/apps/dependabot"><code>@​dependabot[bot]</code></a></li>
</ul>
<!-- raw HTML omitted -->
<h2>Bug Fixes</h2>
<ul>
<li>fix: preserve proxy-aware fetch in octokit client (<a href="">#1682</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<h2>Maintenance</h2>
<ul>
<li>chore: update references to branch master to main (<a href="">#1686</a>) <a href="https://github.com/cchanche"><code>@​cchanche</code></a></li>
<li>ci: rely on conventional pr titles (<a href="">#1685</a>) <a href="https://github.com/cchanche"><code>@​cchanche</code></a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li>No new contributors</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/release-drafter/release-drafter/compare/v7.6.0...v7.7.0">https://github.com/release-drafter/release-drafter/compare/v7.6.0...v7.7.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>34d8067</code></a> chore: release v7.7.0</li>
<li><a href=""><code>cd773d2</code></a> style: format and lint docs</li>
<li><a href=""><code>14d2d94</code></a> feat: no new contributor template (<a href="">#1687</a>)</li>
<li><a href=""><code>94daa9e</code></a> chore: update references to branch master to main (<a href="">#1686</a>)</li>
<li><a href=""><code>b195e66</code></a> ci: rely on conventional pr titles (<a href="">#1685</a>)</li>
<li><a href=""><code>246878a</code></a> build(deps-dev): bump postcss from 8.5.17 to 8.5.23 (<a href="">#1683</a>)</li>
<li><a href=""><code>c3acaa7</code></a> fix: preserve proxy-aware fetch in octokit client (<a href="">#1682</a>)</li>
<li><a href=""><code>22a22c8</code></a> chore(deps): update npm tool constraint to 12.0.1 (<a href="">#1668</a>)</li>
<li><a href=""><code>133e592</code></a> chore(deps): update npm tool constraint to 11.18.0 (<a href="">#1665</a>)</li>
<li><a href=""><code>b806fc0</code></a> chore(deps): update node.js to v24.18.0 (<a href="">#1664</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/release-drafter/release-drafter/compare/eada3c96a64734dd381cfbda23511034e328ddb0...34d80673e067bdc0c24568d3af899c216adcfaa9">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f9bb56f87616`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.