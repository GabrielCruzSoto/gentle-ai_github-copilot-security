# Architecture: Gentle AI for GitHub Copilot

## 1. Overview & Core Philosophy

**gentle-ai-copilot** adapts the proven principles of the Gentle AI ecosystem for corporate and banking environments where developers use **VS Code + GitHub Copilot** and external third-party tools, agents, or CLI daemons are restricted.

Traditional agent harness platforms rely on external daemons, background MCP servers, and language-specific runtimes (Node, Python, Go) that frequently violate bank security baselines.

`gentle-ai-copilot` achieves the exact same architectural rigor using **100% native VS Code and GitHub Copilot configuration files and Git-backed Markdown artifacts**:

```
┌─────────────────────────────────────────────────────────────┐
│                    VS Code + GitHub Copilot                 │
│                                                             │
│   ┌────────────────────────┐    ┌──────────────────────┐    │
│   │ .github/copilot-       │    │ .github/prompts/     │    │
│   │ instructions.md        │    │ *.prompt.md          │    │
│   │ (Global Rules & Guard) │    │ (Specialized Agents) │    │
│   └───────────┬────────────┘    └──────────┬───────────┘    │
└───────────────┼────────────────────────────┼────────────────┘
                │                            │
                ▼                            ▼
┌─────────────────────────────────────────────────────────────┐
│                   Zero-External-Tool Harness                │
│                                                             │
│   odd/tasks/              odd/evidence/         skills/     │
│   (ODD Task Specs)        (4R Review Ledgers)   (Skills)    │
└─────────────────────────────────────────────────────────────┘
```

## 2. Core Pillars

| Pillar | In Gentle AI CLI | In Gentle AI Copilot |
|---|---|---|
| **Memory** | Engram daemon + SQLite MCP | Git history + `odd/tasks/` + in-repo task logs |
| **Workflow** | ODD protocol via Go runtime | `.github/copilot-instructions.md` + `/odd-spec` + `/tdd-cycle` |
| **Evidence** | `gentle-ai review` CLI receipts | `.github/prompts/review-4r.prompt.md` + `odd/evidence/*.md` |
| **Security** | Runtime sandbox / permissions | Zero third-party binaries, airgap-ready, OWASP banking checks |

## 3. Specialized Copilot Agents / Prompts

VS Code Prompt Files (`.github/prompts/*.prompt.md`) provide isolated, specialized personas callable directly in Copilot Chat:

1. **`orchestrator`**: The senior architect enforcing ODD, TDD, and work unit budgets.
2. **`odd-spec`**: Generates and refines feature tasks before implementation.
3. **`tdd-cycle`**: Guides the strict Red -> Green -> Refactor cycle.
4. **`review-4r`**: Multi-lens reviewer (Risk, Readability, Reliability, Resilience).
5. **`review-refuter`**: Adversarial counter-evidence verification of blocker findings.
6. **`banking-security`**: Audits against OWASP, data leakage, and financial compliance.
7. **`work-unit-commit`**: Packages changes into atomic commits under 400 lines.
