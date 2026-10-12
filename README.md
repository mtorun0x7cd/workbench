<!--
SPDX-FileCopyrightText: 2026 Mert Torun
SPDX-License-Identifier: MIT
-->

# Workbench

A sandbox for trying GitHub Actions workflows, repository settings and rulesets, issue and pull request flows, and releases before they reach the repositories of my published work. Those repositories are records, and every commit stays in their history; here a failed attempt costs nothing.

[![License: MIT](https://img.shields.io/badge/License-MIT-1D4ED8?style=flat)](LICENSE)

## How it is used

Every experiment starts as an issue and is carried out in a pull request. I work here alone, so my pull requests are merged without review. What holds here is then carried over. Others may open issues and pull requests as well; a reply is not guaranteed.

## Experiments

| Issue | Pull request | Date | What was tried | Result | Carried to the published works |
| --- | --- | --- | --- | --- | --- |
| [#1](https://github.com/mtorun0x7cd/workbench/issues/1) | [#2](https://github.com/mtorun0x7cd/workbench/pull/2) | 2026-10-09 | A Markdown lint and a secret scan on every pull request and every push to `main` | Both checks passed ([runs](https://github.com/mtorun0x7cd/workbench/pull/2/checks)). They were not required checks, so the merge at 16:41:11 UTC did not wait for the Markdown lint, which finished at 16:41:18 UTC; the secret scan had finished at 16:41:10 UTC. | Not yet. The works run the same two checks with markdownlint-cli2 0.23.0; this repository runs 0.23.3. |
| [#3](https://github.com/mtorun0x7cd/workbench/issues/3) | [#4](https://github.com/mtorun0x7cd/workbench/pull/4) | 2026-10-12 | A review requested from a collaborator and still outstanding when the pull request is merged | Both checks passed ([runs](https://github.com/mtorun0x7cd/workbench/pull/4/checks)), the secret scan at 13:52:27 UTC and the Markdown lint at 13:52:32 UTC. The review had been requested at 13:52:12 UTC and was still outstanding at the merge at 13:52:39 UTC. The profile showed YOLO at the first look afterwards, at 13:53:00 UTC. [#2](https://github.com/mtorun0x7cd/workbench/pull/2) was merged without a requested review and had not earned YOLO 68 hours later. | No; it concerns the profile, not the works. |

Repository rulesets, the merge and retention settings, and releases have not been tried here yet.

## Checks

Every pull request and every push to `main` runs two checks, and both can also be started by hand from the Actions tab:

- Markdown lint, with markdownlint-cli2 and the rules of [`.markdownlint.jsonc`](.markdownlint.jsonc);
- a secret scan of the whole history, with gitleaks and the rules of [`.gitleaks.toml`](.gitleaks.toml).

The action is pinned to a full commit SHA, markdownlint-cli2 to a version, and gitleaks to a version and its SHA-256. Each job stops after ten minutes. A newer run on the same pull request cancels the older one. On `main` a run that has started is not cancelled; the run of a later push waits for it.

## Run the checks locally

The two commands the checks run:

```sh
npx --yes markdownlint-cli2@0.23.3 "**/*.md"
gitleaks git --redact --config .gitleaks.toml .
```

The hook in `.githooks/pre-commit` scans the staged changes with gitleaks. Where gitleaks is not installed, it prints a warning and lets the commit pass.

## Achievements

Working this way also earns some of GitHub's profile achievements, such as Quickdraw for closing an issue within five minutes of opening it, and YOLO for merging a pull request without a review. Here a merge with no review requested did not earn YOLO, and one with a requested review still outstanding did ([#3](https://github.com/mtorun0x7cd/workbench/issues/3)). The achievements are not why this repository exists, and they are not hidden either: an issue or pull request that earns one says so.

## Contents

| Path | Content |
| --- | --- |
| `.github/workflows/` | the two checks, `docs.yml` and `secret-scan.yml` |
| `.github/FUNDING.yml` | the sponsor links of the account; inactive here, because the Sponsor button is turned off for this repository |
| `.githooks/pre-commit` | a secret scan of the staged changes with gitleaks; enable it in a clone with `git config core.hooksPath .githooks` |
| `docs/social/` | the social card, and `render.sh`, which renders it with rsvg-convert |
| `.editorconfig` | character set, line endings and indentation for editors |
| `.gitattributes` | line endings and binary files for Git |
| `.gitignore` | editor and operating system files that Git leaves out |
| `.gitleaks.toml` | the rules of the secret scan |
| `.markdownlint.jsonc` | the rules of the Markdown lint |
| [`LICENSE`](LICENSE) | the MIT License |
| [`SECURITY.md`](SECURITY.md) | how to report a security problem |

## License

[MIT](LICENSE)

## Contact

Mert Torun, [info@mtorun0x7cd.com](mailto:info@mtorun0x7cd.com)
