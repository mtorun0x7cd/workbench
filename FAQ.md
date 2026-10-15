<!--
SPDX-FileCopyrightText: 2026 Mert Torun
SPDX-License-Identifier: MIT
-->

# Frequently asked questions

Two questions from the repository's discussions, each with the answer marked there.

## Why scan the whole history for secrets?

> The secret scan checks out the full history and runs gitleaks over all of it. Wouldn't it be enough to scan only the commits of a pull request?

Scanning only the commits of a pull request would check each commit once, with the rules of that day. A rule added to `.gitleaks.toml` later, or a newer version of gitleaks, would never see the older commits, and a commit that reached main without a pull request would not be checked at all. A secret in any of them stays readable in the history even after a later commit removes it. The full scan checks every commit on every run, and in a repository this small that stays cheap.

From [discussion #5](https://github.com/mtorun0x7cd/workbench/discussions/5).

## Running the Markdown check locally

> Is there a simple way to run the Docs check on my machine before I push, so a pull request doesn't fail on it?

Yes. From the root of the repository run `npx --yes markdownlint-cli2@0.23.3 "**/*.md"`. That is the same version with the same rules from `.markdownlint.jsonc` as the Docs workflow, so if it passes on your machine, it passes on the pull request too.

From [discussion #6](https://github.com/mtorun0x7cd/workbench/discussions/6).
