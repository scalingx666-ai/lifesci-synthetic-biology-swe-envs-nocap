# Issue

**Title:** Bump the actions-deps group with 5 updates

## Description

Bumps the actions-deps group with 5 updates:

| Package | From | To |
| --- | --- | --- |
| [actions/checkout](https://github.com/actions/checkout) | `7.0.0` | `7.0.1` |
| [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv) | `8.3.2` | `9.0.0` |
| [pypa/gh-action-pypi-publish](https://github.com/pypa/gh-action-pypi-publish) | `1.14.0` | `1.14.1` |
| [release-drafter/release-drafter](https://github.com/release-drafter/release-drafter) | `7.5.1` | `7.6.0` |
| [actions/setup-python](https://github.com/actions/setup-python) | `6.3.0` | `7.0.0` |

Updates `actions/checkout` from 7.0.0 to 7.0.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/checkout/releases">actions/checkout's releases</a>.</em></p>
<blockquote>
<h2>v7.0.1</h2>
<h2>What's Changed</h2>
<ul>
<li>skip running unsafe pr check if input is default by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2518</a></li>
<li>trim only ascii whitespace for branch by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2521</a></li>
<li>escape values passed to --unset by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2530</a></li>
<li>Various dependency updates</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/checkout/compare/v7...v7.0.1">https://github.com/actions/checkout/compare/v7...v7.0.1</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/actions/checkout/blob/main/CHANGELOG.md">actions/checkout's changelog</a>.</em></p>
<blockquote>
<h1>Changelog</h1>
<h2>v7.0.1</h2>
<ul>
<li>Skip running unsafe pr check if input is default by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2518</a></li>
<li>Trim only ascii whitespace for branch by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2521</a></li>
<li>Escape values passed to --unset by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2530</a></li>
<li>Various dependency updates</li>
</ul>
<h2>v7.0.0</h2>
<ul>
<li>Block checking out fork PR for pull_request_target and workflow_run by <a href="https://github.com/aiqiaoy"><code>@​aiqiaoy</code></a> in <a href="">actions/checkout#2454</a></li>
<li>Various dependency updates</li>
</ul>
<h2>v6.0.3</h2>
<ul>
<li>Fix checkout init for SHA-256 repositories by <a href="https://github.com/yaananth"><code>@​yaananth</code></a> in <a href="">actions/checkout#2439</a></li>
<li>fix: expand merge commit SHA regex and add SHA-256 test cases by <a href="https://github.com/yaananth"><code>@​yaananth</code></a> in <a href="">actions/checkout#2414</a></li>
</ul>
<h2>v6.0.2</h2>
<ul>
<li>Fix tag handling: preserve annotations and explicit fetch-tags by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2356</a></li>
</ul>
<h2>v6.0.1</h2>
<ul>
<li>Add worktree support for persist-credentials includeIf by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2327</a></li>
</ul>
<h2>v6.0.0</h2>
<ul>
<li>Persist creds to a separate file by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2286</a></li>
<li>Update README to include Node.js 24 support details and requirements by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/checkout#2248</a></li>
</ul>
<h2>v5.0.1</h2>
<ul>
<li>Port v6 cleanup to v5 by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2301</a></li>
</ul>
<h2>v5.0.0</h2>
<ul>
<li>Update actions checkout to use node 24 by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/checkout#2226</a></li>
</ul>
<h2>v4.3.1</h2>
<ul>
<li>Port v6 cleanup to v4 by <a href="https://github.com/ericsciple"><code>@​ericsciple</code></a> in <a href="">actions/checkout#2305</a></li>
</ul>
<h2>v4.3.0</h2>
<ul>
<li>docs: update README.md by <a href="https://github.com/motss"><code>@​motss</code></a> in <a href="">actions/checkout#1971</a></li>
<li>Add internal repos for checking out multiple repositories by <a href="https://github.com/mouismail"><code>@​mouismail</code></a> in <a href="">actions/checkout#1977</a></li>
<li>Documentation update - add recommended permissions to Readme by <a href="https://github.com/benwells"><code>@​benwells</code></a> in <a href="">actions/checkout#2043</a></li>
<li>Adjust positioning of user email note and permissions heading by <a href="https://github.com/joshmgross"><code>@​joshmgross</code></a> in <a href="">actions/checkout#2044</a></li>
<li>Update README.md by <a href="https://github.com/nebuk89"><code>@​nebuk89</code></a> in <a href="">actions/checkout#2194</a></li>
<li>Update CODEOWNERS for actions by <a href="https://github.com/TingluoHuang"><code>@​TingluoHuang</code></a> in <a href="">actions/checkout#2224</a></li>
<li>Update package dependencies by <a href="https://github.com/salmanmkc"><code>@​salmanmkc</code></a> in <a href="">actions/checkout#2236</a></li>
</ul>
<h2>v4.2.2</h2>
<ul>
<li><code>url-helper.ts</code> now leverages well-known environment variables by <a href="https://github.com/jww3"><code>@​jww3</code></a> in <a href="">actions/checkout#1941</a></li>
<li>Expand unit test coverage for <code>isGhes</code> by <a href="https://github.com/jww3"><code>@​jww3</code></a> in <a href="">actions/checkout#1946</a></li>
</ul>
<h2>v4.2.1</h2>
<ul>
<li>Check out other refs/* by commit if provided, fall back to ref by <a href="https://github.com/orhantoy"><code>@​orhantoy</code></a> in <a href="">actions/checkout#1924</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3d3c42e</code></a> prep v7.0.1 release (<a href="">#2531</a>)</li>
<li><a href=""><code>2880268</code></a> escape values passed to --unset (<a href="">#2530</a>)</li>
<li><a href=""><code>12cd223</code></a> trim only ascii whitespace for branch (<a href="">#2521</a>)</li>
<li><a href=""><code>62661c4</code></a> skip running unsafe pr check if input is default (<a href="">#2518</a>)</li>
<li><a href=""><code>e8d4307</code></a> Bump the minor-actions-dependencies group with 2 updates (<a href="">#2499</a>)</li>
<li><a href=""><code>631c942</code></a> eslint 9 (<a href="">#2474</a>)</li>
<li><a href=""><code>4f1f4ae</code></a> Bump actions/upload-artifact from 4 to 7 (<a href="">#2476</a>)</li>
<li><a href=""><code>ba09753</code></a> Bump actions/checkout from 6 to 7 (<a href="">#2488</a>)</li>
<li><a href=""><code>b9e0990</code></a> Bump docker/login-action from 3.3.0 to 4.2.0 (<a href="">#2479</a>)</li>
<li><a href=""><code>e8cb398</code></a> Bump docker/build-push-action from 6.5.0 to 7.2.0 (<a href="">#2478</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/actions/checkout/compare/9c091bb21b7c1c1d1991bb908d89e4e9dddfe3e0...3d3c42e5aac5ba805825da76410c181273ba90b1">compare view</a></li>
</ul>
</details>
<br />

Updates `astral-sh/setup-uv` from 8.3.2 to 9.0.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/astral-sh/setup-uv/releases">astral-sh/setup-uv's releases</a>.</em></p>
<blockquote>
<h2>v9.0.0 🌈 Change <code>prune-cache</code> default to <code>false</code></h2>
<h2>Changes</h2>
<p>This release disables the default cache cache pruning to ease the load on the PyPi infrastructure.
Since users might experience more GitHub Actions cache usage which might result in higher costs this is marked as a breaking change. To read more on why we did this (now) you can read the detailed analysis and reasoning in <a href="">#967</a></p>
<p>Besides this big breaking change we also have a small bugfix while building caches for linux distributions that behave a big different than the &quot;big ones&quot; and a speed up in version resolution by only reading the version manifest until a matching version is found saving runtime and network bandwith.</p>
<h2>🚨 Breaking changes</h2>
<ul>
<li>Change <code>prune-cache</code> default to <code>false</code> <a href="https://github.com/charliermarsh"><code>@​charliermarsh</code></a> (<a href="">#967</a>)</li>
</ul>
<h2>🐛 Bug fixes</h2>
<ul>
<li>fix: fall back to distribution ID when os-release has no version field <a href="https://github.com/cxzhong"><code>@​cxzhong</code></a> (<a href="">#961</a>)</li>
</ul>
<h2>🚀 Enhancements</h2>
<ul>
<li>Speed up version client by partial response reads <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#807</a>)</li>
</ul>
<h2>🧰 Maintenance</h2>
<ul>
<li>chore: update known checksums for 0.11.30 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#968</a>)</li>
<li>chore: update known checksums for 0.11.29 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#960</a>)</li>
</ul>
<h2>📚 Documentation</h2>
<ul>
<li>docs: update version references to v8.3.2 @<a href="https://github.com/apps/github-actions">github-actions[bot]</a> (<a href="">#949</a>)</li>
</ul>
<h2>⬆️ Dependency updates</h2>
<ul>
<li>chore(deps): roll up Dependabot updates <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#970</a>)</li>
<li>chore(deps): roll up Dependabot updates <a href="https://github.com/eifinger"><code>@​eifinger</code></a> (<a href="">#962</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c771a70</code></a> chore(deps): roll up Dependabot updates (<a href="">#970</a>)</li>
<li><a href=""><code>2f537ca</code></a> chore: update known checksums for 0.11.30 (<a href="">#968</a>)</li>
<li><a href=""><code>2269552</code></a> Speed up version client by partial response reads (<a href="">#807</a>)</li>
<li><a href=""><code>47a7f4f</code></a> Change <code>prune-cache</code> default to <code>false</code> (<a href="">#967</a>)</li>
<li><a href=""><code>71966ef</code></a> chore(deps): roll up Dependabot updates (<a href="">#962</a>)</li>
<li><a href=""><code>f12b1f0</code></a> fix: fall back to distribution ID when os-release has no version field (<a href="">#961</a>)</li>
<li><a href=""><code>ecd24dd</code></a> chore: update known checksums for 0.11.29 (<a href="">#960</a>)</li>
<li><a href=""><code>6a19136</code></a> docs: update version references to v8.3.2 (<a href="">#949</a>)</li>
<li>See full diff in <a href="https://github.com/astral-sh/setup-uv/compare/11f9893b081a58869d3b5fccaea48c9e9e46f990...c771a70e6277c0a99b617c7a806ffedaca235ff9">compare view</a></li>
</ul>
</details>
<br />

Updates `pypa/gh-action-pypi-publish` from 1.14.0 to 1.14.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pypa/gh-action-pypi-publish/releases">pypa/gh-action-pypi-publish's releases</a>.</em></p>
<blockquote>
<h2>v1.14.1</h2>
<!-- raw HTML omitted -->
<h2>🛠️ Internal Dependencies</h2>
<p><a href="https://github.com/adisivaprasad"><code>@​adisivaprasad</code></a><a href="https://github.com/sponsors/adisivaprasad">💰</a> helped get rid of the GitHub Actions runner warning about the old Node 20 runtime being used by updating <code>actions/setup-python</code> from v5.6.0 to v6.2.0 in <a href="">#408</a>.</p>
<h2>💪 New Contributors</h2>
<ul>
<li><a href="https://github.com/adisivaprasad"><code>@​adisivaprasad</code></a> made their first contribution in <a href="">#408</a></li>
<li><a href="https://github.com/jylenhof"><code>@​jylenhof</code></a><a href="https://github.com/sponsors/jylenhof">💰</a> followed up and reminded us to actually cut this release in <a href="">#413</a></li>
</ul>
<p><strong>🪞 Full Diff</strong>: <a href="https://github.com/pypa/gh-action-pypi-publish/compare/v1.14.0...v1.14.1">https://github.com/pypa/gh-action-pypi-publish/compare/v1.14.0...v1.14.1</a></p>
<p><strong>🧔‍♂️ Release Manager:</strong> <a href="https://github.com/sponsors/webknjaz"><code>@​webknjaz</code></a> <a href="https://stand-with-ukraine.pp.ua">🇺🇦</a></p>
<p><strong>🙏 Special Thanks</strong> to <a href="https://github.com/jylenhof"><code>@​jylenhof</code></a><a href="https://github.com/sponsors/jylenhof">💰</a> for reminding me to work on this release!</p>
<p><strong>💬 Discuss</strong> <a href="https://bsky.app/profile/did:plc:ve6s3mxkefjaxty3m4fdqumn/post/3mrd7jpnxc22d">on Bluesky 🦋</a>, <a href="https://mastodon.social/@webknjaz/116970132515797444">on Mastodon 🐘</a> and <a href="https://github.com/pypa/gh-action-pypi-publish/discussions/414">on GitHub</a>.</p>
<p><a href="https://github.com/sponsors/webknjaz"><img src="https://img.shields.io/badge/%40webknjaz-transparent?logo=githubsponsors&amp;logoColor=%23EA4AAA&amp;label=Sponsor&amp;color=2a313c" alt="GH Sponsors badge" /></a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ba38be9</code></a> Merge pull request <a href="">#408</a> from adisivaprasad/bump-setup-python-v6</li>
<li><a href=""><code>a6c5088</code></a> Bump actions/setup-python from v5.6.0 to v6.2.0</li>
<li>See full diff in <a href="https://github.com/pypa/gh-action-pypi-publish/compare/cef221092ed1bacb1cc03d23a2d87d1d172e277b...ba38be9e461d3875417946c167d0b5f3d385a247">compare view</a></li>
</ul>
</details>
<br />

Updates `release-drafter/release-drafter` from 7.5.1 to 7.6.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/release-drafter/release-drafter/releases">release-drafter/release-drafter's releases</a>.</em></p>
<blockquote>
<h2>v7.6.0</h2>
<h1>What's Changed</h1>
<h2>New</h2>
<ul>
<li>feat: resolve release commitish refs to commit SHAs (<a href="">#1649</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat: add new contributors list (<a href="">#1645</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat: support pull request co-authors (<a href="">#1646</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>feat: support per-key merge strategies in <code>_extends</code> (<a href="">#1642</a>) <a href="https://github.com/ReneWerner87"><code>@​ReneWerner87</code></a>, <a href="https://github.com/cchanche"><code>@​cchanche</code></a>, <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<h2>Bug Fixes</h2>
<ul>
<li>fix: .github in legacy <code>_extends</code> refs (<a href="">#1650</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>fix: normalize release target branch refs (<a href="">#1648</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
<li>fix: duplicate and skipped release contributors (<a href="">#1644</a>) <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<h2>Maintenance</h2>
<ul>
<li>chore(deps): update dependency typescript to 7.0.2 (<a href="">#1667</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>ci(deps): update github/codeql-action digest to 7188fc3 (<a href="">#1654</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>ci(deps): update actions/stale digest to 1e223db (<a href="">#1653</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update dependency <code>@​types/node</code> to 24.13.3 (<a href="">#1661</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update vitest to 4.1.10 (<a href="">#1656</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update graphql-codegen (<a href="">#1663</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update dependency vite to 8.1.4 (<a href="">#1662</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a>, <a href="https://github.com/apps/github-actions"><code>@​github-actions[bot]</code></a></li>
<li>chore(deps): update dependency nock to 14.0.16 (<a href="">#1655</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore(deps): update dependency <code>@​biomejs/biome</code> to 2.5.3 (<a href="">#1660</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>ci(deps): update actions/checkout action to v7.0.0 (<a href="">#1669</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>ci(deps): update actions/setup-node action to v7.0.0 (<a href="">#1670</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
<li>chore: update generated GraphQL types (<a href="">#1641</a>) <a href="https://github.com/apps/github-actions"><code>@​github-actions[bot]</code></a>, <a href="https://github.com/jetersen"><code>@​jetersen</code></a></li>
</ul>
<h2>Dependency Updates</h2>
<ul>
<li>fix(deps): update dependency graphql to 16.14.2 (<a href="">#1657</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a>, <a href="https://github.com/apps/github-actions"><code>@​github-actions[bot]</code></a></li>
<li>fix(deps): update dependency yaml to 2.9.0 (<a href="">#1666</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a>, <a href="https://github.com/apps/github-actions"><code>@​github-actions[bot]</code></a></li>
<li>fix(deps): update dependency semver to 7.8.5 (<a href="">#1659</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a>, <a href="https://github.com/apps/github-actions"><code>@​github-actions[bot]</code></a></li>
<li>fix(deps): update dependency ignore to 7.0.6 (<a href="">#1658</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a>, <a href="https://github.com/apps/github-actions"><code>@​github-actions[bot]</code></a></li>
<li>chore(deps): update dependency <code>@​biomejs/biome</code> to 2.5.3 (<a href="">#1660</a>) <a href="https://github.com/apps/renovate"><code>@​renovate[bot]</code></a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/ReneWerner87"><code>@​ReneWerner87</code></a> made their first contribution in <a href="">#1642</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/release-drafter/release-drafter/compare/v7.5.1...v7.6.0">https://github.com/release-drafter/release-drafter/compare/v7.5.1...v7.6.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>eada3c9</code></a> chore: release v7.6.0</li>
<li><a href=""><code>4621843</code></a> migrate biome config</li>
<li><a href=""><code>e9aeda7</code></a> chore(deps): update dependency typescript to 7.0.2 (<a href="">#1667</a>)</li>
<li><a href=""><code>c943e7c</code></a> fix(deps): update dependency graphql to 16.14.2 (<a href="">#1657</a>)</li>
<li><a href=""><code>b9af925</code></a> fix(deps): update dependency yaml to 2.9.0 (<a href="">#1666</a>)</li>
<li><a href=""><code>f4aa158</code></a> ci(deps): update github/codeql-action digest to 7188fc3 (<a href="">#1654</a>)</li>
<li><a href=""><code>9397385</code></a> ci(deps): update actions/stale digest to 1e223db (<a href="">#1653</a>)</li>
<li><a href=""><code>5dd9f21</code></a> chore(deps): update dependency <code>@​types/node</code> to 24.13.3 (<a href="">#1661</a>)</li>
<li><a href=""><code>903a9a1</code></a> chore(deps): update vitest to 4.1.10 (<a href="">#1656</a>)</li>
<li><a href=""><code>2796d1b</code></a> fix(deps): update dependency semver to 7.8.5 (<a href="">#1659</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/release-drafter/release-drafter/compare/4d75298e00d9e34c483e5ff8c68d0ea1c1940c1e...eada3c96a64734dd381cfbda23511034e328ddb0">compare view</a></li>
</ul>
</details>
<br />

Updates `actions/setup-python` from 6.3.0 to 7.0.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/actions/setup-python/releases">actions/setup-python's releases</a>.</em></p>
<blockquote>
<h2>v7.0.0</h2>
<h2>What's Changed</h2>
<h3>Enhancements</h3>
<ul>
<li>Migrate to ESM and upgrade dependencies by <a href="https://github.com/priyagupta108"><code>@​priyagupta108</code></a> in <a href="">actions/setup-python#1330</a></li>
<li>Pin SHA commits and update docs with latest versions by <a href="https://github.com/HarithaVattikuti"><code>@​HarithaVattikuti</code></a> in <a href="">actions/setup-python#1338</a></li>
<li>Remove the pip-install input by <a href="https://github.com/gowridurgad"><code>@​gowridurgad</code></a> in <a href="">actions/setup-python#1336</a></li>
</ul>
<h3>Bug Fix</h3>
<ul>
<li>Fix to Classify stderr warning messages as warnings instead of errors in annotations by <a href="https://github.com/lmvysakh"><code>@​lmvysakh</code></a> in <a href="">actions/setup-python#1335</a></li>
<li>Validate and retry manifest fetch to prevent silent failures by <a href="https://github.com/priyagupta108"><code>@​priyagupta108</code></a> in <a href="">actions/setup-python#1332</a></li>
</ul>
<h3>Dependency Upgrade</h3>
<ul>
<li>Bump certifi from 2020.6.20 to 2024.7.4 in /<strong>tests</strong>/data by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">actions/setup-python#1328</a></li>
<li>Remove EOL Python versions and Bumps numpy text fixture by <a href="https://github.com/priya-kinthali"><code>@​priya-kinthali</code></a> in <a href="">actions/setup-python#1333</a></li>
<li>Upgrade <code>@​actions/cache</code> to 6.2.0 by <a href="https://github.com/philip-gai"><code>@​philip-gai</code></a> in <a href="">actions/setup-python#1337</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/lmvysakh"><code>@​lmvysakh</code></a> made their first contribution in <a href="">actions/setup-python#1335</a></li>
<li><a href="https://github.com/philip-gai"><code>@​philip-gai</code></a> made their first contribution in <a href="">actions/setup-python#1337</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/actions/setup-python/compare/v6...v7.0.0">https://github.com/actions/setup-python/compare/v6...v7.0.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5fda3b9</code></a> Pin SHA commits and update docs with latest versions (<a href="">#1338</a>)</li>
<li><a href=""><code>4ab7e95</code></a> Merge pull request <a href="">#1337</a> from actions/philip-gai/bump-actions-cache-6-2-0</li>
<li><a href=""><code>0f3a009</code></a> Remove the pip-install input (<a href="">#1336</a>)</li>
<li><a href=""><code>f8cf429</code></a> Migrate to ESM and upgrade dependencies (<a href="">#1330</a>)</li>
<li><a href=""><code>54baeea</code></a> Validate and retry manifest fetch to prevent silent failures (<a href="">#1332</a>)</li>
<li><a href=""><code>c709277</code></a> Annotation code fix (<a href="">#1335</a>)</li>
<li><a href=""><code>6849080</code></a> remove EOL Python versions and Bumps numpy text fixture (<a href="">#1333</a>)</li>
<li><a href=""><code>0903b46</code></a> Bump certifi from 2020.6.20 to 2024.7.4 in /<strong>tests</strong>/data (<a href="">#1328</a>)</li>
<li>See full diff in <a href="https://github.com/actions/setup-python/compare/ece7cb06caefa5fff74198d8649806c4678c61a1...5fda3b95a4ea91299a34e894583c3862153e4b97">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84a701ab2580`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.