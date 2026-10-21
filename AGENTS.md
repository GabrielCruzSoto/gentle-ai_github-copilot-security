# AGENTS.md — Gentle AI Copilot Harness

## Overview
This repository contains the **Gentle AI Copilot Harness**, specifically designed for enterprise and banking environments utilizing **VS Code + GitHub Copilot** with zero third-party external tools or daemons.

---

## Copilot Roles & Prompt Index (`.github/prompts/`)

| Prompt File | Role | Primary Trigger / Purpose |
|---|---|---|
| `orchestrator.prompt.md` | Master Orchestrator | End-to-end feature lifecycle, architecture coordination, work continuity |
| `odd-spec.prompt.md` | ODD Spec Specialist | Creating/updating task specs in `odd/tasks/<feature>.md` |
| `tdd-cycle.prompt.md` | Strict TDD Engineer | Enforcing the Red -> Green -> Refactor cycle |
| `review-4r.prompt.md` | 4R Reviewer | Running Risk, Readability, Reliability, Resilience review sweeps |
| `review-refuter.prompt.md` | Adversarial Refuter | Challenging and verifying blocker/critical review claims |
| `banking-security.prompt.md` | Banking Security Auditor | OWASP Top 10, PII/PCI leakage prevention, financial safety invariants |
| `work-unit-commit.prompt.md` | Work Unit Commit Specialist | Formatting atomic Conventional Commits under 400 lines |

---

## Skills Index (`skills/` & `.github/skills/`)

Before executing specific tasks, consult the matching skill:

| Skill | Path | Activation Trigger |
|---|---|---|
| `work-unit-commits` | `skills/work-unit-commits/SKILL.md` | Sizing commits, conventional commits, packaging changes |
| `branch-pr` | `skills/branch-pr/SKILL.md` | Creating branches, writing PR descriptions, audit traceability |
| `chained-pr` | `skills/chained-pr/SKILL.md` | Slicing large features (>400 lines) into chained review PRs |
| `cognitive-doc-design` | `skills/cognitive-doc-design/SKILL.md` | Writing scannable, high-density documentation and specs |
| `comment-writer` | `skills/comment-writer/SKILL.md` | Writing in-code justification comments and review feedback |
| `issue-root-resolution` | `skills/issue-root-resolution/SKILL.md` | Reproducing and fixing bugs at the structural root |
| `systemic-issue-triage` | `skills/systemic-issue-triage/SKILL.md` | Clustering bug reports by invariant; preventing patch bloat |
| `banking-security-audit` | `skills/banking-security-audit/SKILL.md` | Auditing payment/financial code, sensitive data handling |
