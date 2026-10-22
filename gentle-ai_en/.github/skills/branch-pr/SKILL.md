---
name: branch-pr
description: "GitFlow branching strategies, PR preparation, issue traceability, and review gates. Trigger: creating branches or PRs."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.1"
---

# Branch & Pull Request Skill (GitFlow Mandatory)

## When to Use

Load this skill whenever:
- Naming or creating branches in Git.
- Establishing base and target branches for code integration.
- Writing PR descriptions in GitHub, GitLab, or enterprise Bitbucket.
- Preparing releases (`release/`) or production hotfixes (`hotfix/`).

## GitFlow Branching Architecture

```
main       ●───────────────────────────────● (v1.0.0)─────────● (v1.0.1)───────● (v1.1.0)
            \                             /                   /                 /
hotfix       \                           /       ●───────────● (hotfix/1.0.1)  /
              \                         /       /             \               /
develop        ●───────────●───────────●───────●───────────────●─────────────●
                \         /             \                                   /
feature          ●───────● (feat/A)      \                                 /
                                          ●───────────────────────────────● (release/1.1.0)
```

## Mandatory Branching Rules

1. **Main & Protected Branches (`prod`, `master`, `main`, `develop`)**:
   - `prod` / `master` / `main`: Official production code. **ZERO DIRECT COMMITS**. Direct pushes or commits to production branches are strictly forbidden. All code must enter via an approved Pull Request (PR) after passing 4R review. Tagged with annotated semantic versions (`vX.Y.Z`).
   - `develop`: Ongoing feature integration branch. **ZERO DIRECT COMMITS**. All features merge here via PR. Starting point for `feature/*` and `release/*`.

2. **Temporary Branches & Naming Conventions**:
   - **Feature Branches (`feature/`)**:
     - *Origin*: `develop`
     - *Target (PR)*: `develop`
     - *Naming*: `feature/<task-id>-<short-description>`
   - **Release Stabilization Branches (`release/`)**:
     - *Origin*: `develop`
     - *Target (PR)*: `main` AND back into `develop`
     - *Naming*: `release/v<X.Y.Z>`
     - *Action on merge*: Create annotated tag `v<X.Y.Z>` on `main`.
   - **Production Hotfix Branches (`hotfix/`)**:
     - *Origin*: `main`
     - *Target (PR)*: `main` AND back into `develop`
     - *Naming*: `hotfix/<incident-id>-<short-description>`
     - *Action on merge*: Create annotated tag `v<X.Y.Z+1>` on `main`.

3. **Requirements Traceability & Banking Audit**:
   - Every `feature` or `hotfix` branch must include the ODD task ID or corporate ticket in its name and PR title.
   - Merging code without an associated ticket and test receipts is forbidden.

4. **PR Description Structure**:
   - **Type & Base Branch**: Explicitly declare branch type and base (`develop` or `main`).
   - **Summary**: Business problem solved.
   - **Verification Receipts**: Automated test suite evidence and 4R review ledger.
   - **Security**: Confirmation of banking compliance (zero PII/PCI exposure, fail-closed access).

5. **Size Budget**:
   - Keep PR diffs bounded within ~400 changed lines. For larger features, split into chained branches using the `chained-pr` skill.
