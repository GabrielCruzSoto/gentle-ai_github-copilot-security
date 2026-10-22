# gentle-ai-copilot

> **Deterministic Harness for VS Code + GitHub Copilot in Restricted Enterprise & Banking Environments**

`gentle-ai-copilot` packages the core architecture, workflow discipline, and review mechanisms of **Gentle AI** into a **zero-third-party-tool, zero-binary, purely declarative configuration** tailored specifically for Visual Studio Code and GitHub Copilot.

---

## 🏛️ Built for Restricted Banking Environments

In financial institutions and regulated corporate networks, unapproved binaries, external MCP servers, background node/python daemons, and outbound cloud calls to third-party AI tools are strictly forbidden.

`gentle-ai-copilot` delivers complete engineering rigor using **only**:
- Native GitHub Copilot instructions (`.github/copilot-instructions.md`).
- Native VS Code prompt files (`.github/prompts/*.prompt.md`).
- Standard Markdown skills (`skills/*/SKILL.md`).
- Git-backed Organic Driven Development (`odd/tasks/` and `odd/evidence/`).

No installations. No external binaries. No security alarms.

---

## 📦 What's Inside

```
gentle-ai-copilot/
├── .github/
│   ├── copilot-instructions.md          # Global rules, response contract, security invariants
│   ├── prompts/                         # VS Code Copilot prompt files (custom roles)
│   │   ├── orchestrator.prompt.md       # Master orchestrator
│   │   ├── odd-spec.prompt.md           # Feature specification writer
│   │   ├── tdd-cycle.prompt.md          # Strict TDD enforcer
│   │   ├── review-4r.prompt.md          # 4R review sweep (Risk, Readability, Reliability, Resilience)
│   │   ├── review-refuter.prompt.md     # Adversarial verifier of blocker findings
│   │   ├── banking-security.prompt.md   # Banking security & OWASP audit
│   │   └── work-unit-commit.prompt.md   # Atomic commits under 400 lines
│   └── skills/                          # Skills catalog accessible via Copilot context
├── odd/
│   ├── TEMPLATE.md                      # Template for feature specs & verification receipts
│   ├── tasks/                           # Active feature specs
│   └── evidence/                        # Review ledgers and test receipts
├── docs/
│   ├── architecture.md                  # System architecture and design principles
│   ├── banking-environment.md           # Banking security & airgap compliance guide
│   ├── gitflow-workflow.md              # GitFlow workflow guide for Copilot and banking
│   ├── vscode-copilot-setup.md          # Step-by-step setup in VS Code
│   ├── odd-workflow.md                  # ODD lifecycle manual
│   └── review-receipts-guide.md         # 4R review framework & evidence ledger
├── AGENTS.md                            # Comprehensive index of roles, prompts, and skills
└── README.md
```

---

## 🚀 Quickstart

1. Copy `.github/`, `odd/`, and `AGENTS.md` into your banking repository.
2. Open the project in VS Code with GitHub Copilot enabled.
3. Ensure the repository has `main` and `develop` branches configured (**GitFlow** model).
4. Open GitHub Copilot Chat and type `/` to access the custom prompts:
   - Run `/odd-spec` to define your feature and branch off `develop`.
   - Run `/tdd-cycle` to develop with strict test-first discipline.
   - Run `/review-4r` to generate a verifiable review ledger.
   - Run `/banking-security` to audit against financial compliance.
   - Run `/work-unit-commit` to generate clean Conventional Commits.

---

## 📚 Documentation

- [Architecture Overview](docs/architecture.md)
- [Banking Compliance & Safety](docs/banking-environment.md)
- [GitFlow Workflow Guide](docs/gitflow-workflow.md)
- [VS Code Copilot Setup Guide](docs/vscode-copilot-setup.md)
- [ODD Workflow Manual](docs/odd-workflow.md)
- [4R Review Framework](docs/review-receipts-guide.md)

---

## 🙏 Credits & Acknowledgements

This project is a specialized adaptation inspired by and derived from **[Gentle AI](https://github.com/Gentleman-Programming/gentle-ai)**, an outstanding open-source deterministic harness for coding agents created and maintained by **[Gentleman Programming](https://github.com/Gentleman-Programming)**.

All original architectural concepts — including **Organic Driven Development (ODD)**, the **4R Review Framework (Risk, Readability, Reliability, Resilience)**, **Verification Receipts**, and the **Senior Architect mindset (Concepts > Code)** — belong to the Gentle AI project. This repository exists to bring those exact same principles into restricted corporate banking environments utilizing purely declarative VS Code + GitHub Copilot configurations without external binaries or third-party daemons.
