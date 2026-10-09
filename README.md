<!--
SPDX-FileCopyrightText: 2026 Mert Torun
SPDX-License-Identifier: MIT
-->

# Workbench

A repository for trying GitHub procedures before they reach the repositories of my published work: workflows and the actions they pin, repository rules, issue and pull request flows, releases. Those repositories are records, and every commit stays in their history; here a failed attempt costs nothing.

[![License: MIT](https://img.shields.io/badge/License-MIT-1D4ED8?style=flat)](LICENSE) [![Status: Active](https://img.shields.io/badge/Status-Active-1D4ED8?style=flat)](https://www.repostatus.org/#active)

## How it is used

Every experiment starts as an issue and is carried out in a pull request. I work here alone, so pull requests are merged without review. What holds here is then carried over.

## Achievements

Working this way also earns some of GitHub's profile achievements, such as Quickdraw for closing an issue within five minutes of opening it, and YOLO for merging a pull request without review. They are not why this repository exists, and they are not hidden either: an issue or pull request that earns one says so.

## Contents

| Path | Content |
| --- | --- |
| `.githooks/pre-commit` | a secret scan of the staged changes with gitleaks; enable it in a clone with `git config core.hooksPath .githooks` |
| `docs/social/` | the social card, and `render.sh`, which renders it with rsvg-convert |

## License

[MIT](LICENSE)

## Contact

Mert Torun, [info@mtorun0x7cd.com](mailto:info@mtorun0x7cd.com)
