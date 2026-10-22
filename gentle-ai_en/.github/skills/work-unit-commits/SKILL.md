---
name: work-unit-commits
description: "Plan commits as reviewable work units. Trigger: implementation, commit splitting, chained PRs, keeping tests and docs with code."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Work Unit Commits Skill

## When to Use

Load this skill when deciding how to structure, split, or package commits before requesting review or creating PRs.

## Hard Rules

1. **400-Line Limit**:
   - Total changed lines (`additions + deletions`) per work unit must remain roughly under 400 lines.
   - Large PRs overwhelm reviewers, dilute scrutiny, and introduce hidden bugs.
2. **Co-location of Tests and Documentation**:
   - Never commit implementation in one commit and tests/documentation in another.
   - Every work unit must be self-verifying: code, tests that assert its behavior, and docs explaining its contracts belong together.
3. **No Intermediate Broken States**:
   - Each commit in git history must compile, pass tests, and leave the repository in a deployable state.
4. **Conventional Commits**:
   - Use standard conventional commits (`feat`, `fix`, `refactor`, `test`, `docs`, `chore`).
   - Use clean imperative summaries without fluff.
5. **No AI Attribution**:
   - Never inject AI generated banners, "Co-Authored-By", or tool signatures into commit messages.
6. **Absolute Prohibition of Commits on Base Branches (`prod`, `master`, `main`, `develop`)**:
   - Never commit directly to protected branches (`prod`, `production`, `master`, `main`, `develop`).
   - All commits must reside on a temporary supporting branch (`feature/*`, `hotfix/*`, `release/*`) and merge exclusively through an approved Pull Request (PR).
