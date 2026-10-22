# VS Code + GitHub Copilot Setup Guide

This guide explains how to enable and use `gentle-ai-copilot` in Visual Studio Code.

---

## 1. Prerequisites

- Visual Studio Code (v1.90 or newer).
- GitHub Copilot and GitHub Copilot Chat extensions installed and authenticated with your corporate/enterprise account.
- No other extensions or CLI tools are required.

---

## 2. Incorporating into a Project

To apply `gentle-ai-copilot` to an existing or new project within the bank:

1. Copy the following directories into the root of your project:
   ```
   .github/
   ├── copilot-instructions.md
   ├── prompts/
   └── skills/
   odd/
   ├── TEMPLATE.md
   ├── tasks/
   └── evidence/
   AGENTS.md
   ```
2. Open the project in VS Code.

---

## 3. How Copilot Loads the Configuration

- **Global Repository Instructions**:
  VS Code Copilot automatically discovers `.github/copilot-instructions.md`. Every query in Copilot Chat and every inline completion will respect the architectural principles, response length rules, and security constraints.
- **Prompt Files (`.prompt.md`)**:
  Prompt files located in `.github/prompts/` appear as executable prompts in the Copilot Chat interface.
  - In Copilot Chat, type `/` or click the prompt icon to run prompts such as:
    - `/orchestrator` — Start an architectural feature plan.
    - `/odd-spec` — Formulate a task spec in `odd/tasks/`.
    - `/tdd-cycle` — Run a Red-Green-Refactor implementation step.
    - `/review-4r` — Run a 4R review ledger over current changes.
    - `/review-refuter` — Challenge and verify blocker findings.
    - `/banking-security` — Audit against banking security invariants.
    - `/work-unit-commit` — Generate conventional commit message under 400 lines.
- **Skills (`skills/` & `.github/skills/`)**:
  Refer to specific skills in Copilot Chat using `#file` (e.g. `#file:skills/work-unit-commits/SKILL.md`) or ask Copilot to consult the skill index in `AGENTS.md`.
