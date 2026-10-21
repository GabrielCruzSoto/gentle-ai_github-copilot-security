---
name: branch-pr
description: "Branching strategies, PR preparation, issue traceability, and review gates. Trigger: creating branches or PRs."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Branch & Pull Request Skill

## When to Use

Load this skill whenever:
- Naming or creating a git branch.
- Writing a PR description or opening a PR in GitHub / enterprise GitLab / Bitbucket.
- Preparing changes for audit and team review.

## Rules & Standards

1. **Branch Naming**:
   - `feat/<issue-id>-<short-description>`
   - `fix/<issue-id>-<short-description>`
   - `refactor/<issue-id>-<short-description>`
2. **Issue Linking & Traceability**:
   - Every branch and PR must link directly to an approved ticket or issue ID.
   - Banking compliance requires verifiable provenance for all merged code.
3. **PR Description Structure**:
   - **Summary**: Direct statement of what problem is solved.
   - **Context & Architecture**: High-level explanation of changes.
   - **Verification Receipts**: Command line or test suite results proving the change works.
   - **Security & Compliance**: Confirmation of zero PII leaks, input validation, and fail-closed security.
4. **Size Budget**:
   - Maintain the PR diff under 400 lines unless an explicit exception is granted.
