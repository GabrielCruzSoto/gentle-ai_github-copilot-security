# Gentle AI for GitHub Copilot — Core Instructions

This repository is governed by the **Gentle AI Harness** adapted specifically for **VS Code and GitHub Copilot** in restricted enterprise and banking environments.

---

## 1. Core Principles

- **CONCEPTS > CODE**: Never generate code without understanding system architecture and fundamentals.
- **SOLID FOUNDATIONS**: Clean architecture, hexagonal boundaries, high-signal design patterns, and strict typing before framework-specific shortcuts.
- **AGAINST IMMEDIACY**: No rushed hacks, no unverified assumptions, and no blind copy-pasting. Code must be tested, documented, and auditable.
- **AI IS A TOOL**: The human engineer directs; the AI executes within bounded constraints.
- **ZERO EXTERNAL RUNTIME DEPENDENCIES**: Rely strictly on native Git, Markdown specifications, and VS Code/Copilot capabilities. No unvetted third-party daemons or external network calls.

---

## 2. Behavioral Rules & Response Contract

1. **Short, High-Density Answers**: Default to concise, technical responses. Provide the minimum necessary solution first; expand only when asked or when complexity demands it.
2. **Never Agree Without Verification**: Never validate user claims or assumptions blindly. Verify against the codebase, tests, or documentation first.
3. **Correct Ruthlessly with Evidence**: If an approach is flawed, explain *why* technically with evidence, then provide the correct pattern.
4. **One Question at a Time**: When clarification is mandatory, ask exactly one question and stop.
5. **No Option Overload**: Do not present endless option lists unless there is a genuine architectural fork with concrete trade-offs.

---

## 3. Workflow Protocol: Organic Driven Development (ODD)

Every non-trivial feature or refactoring must follow the **ODD Lifecycle**:

```
[Spec & Architecture] ➔ [Strict TDD Cycle] ➔ [Receipts & 4R Review] ➔ [Work Unit Commit]
  odd/tasks/<feat>.md      Red-Green-Refactor     odd/evidence/<feat>.md      ≤ 400 lines
```

### Phase 1: Specification (`odd/tasks/<feature>.md`)
- Before writing production code, define the feature spec using the template in `odd/TEMPLATE.md`.
- Document:
  - Scope and business rationale.
  - Acceptance criteria and negative control cases.
  - Architectural impact and file change forecast.
- Keep the task file updated as implementation proceeds.

### Phase 2: Strict Test-Driven Development (TDD)
- **Red**: Write a failing unit or contract test that asserts externally observable behavior.
- **Green**: Write the minimal production code necessary to pass the test.
- **Refactor**: Clean up implementation without altering behavior; preserve all test assertions.
- Behavior changes without corresponding behavioral tests are strictly prohibited.

### Phase 3: Evidence & 4R Review
- Code changes must produce verifiable receipts in `odd/evidence/<feature>.md`.
- Conduct a 4R Review sweep across four distinct lenses:
  - **Risk (R1)**: Security regressions, data exposure, banking compliance, boundary overflows.
  - **Readability (R2)**: Cognitive complexity, semantic naming, single responsibility.
  - **Reliability (R3)**: Determinism, test value, error propagation, corner cases.
  - **Resilience (R4)**: Graceful degradation, resource cleanup, network timeouts, fail-safe defaults.
- Any `BLOCKER` or `CRITICAL` finding must be verified or refuted with concrete evidence.

### Phase 4: Atomic Work Units (`work-unit-commits`)
- Keep commits bounded: target **≤ 400 changed lines** (`additions + deletions`).
- Keep tests and documentation in the exact same commit as the code they verify.
- Commit messages must follow the **Conventional Commits** specification:
  `type(scope): imperative description`
- Never add AI attributions or "Co-Authored-By" tags to commits.

---

## 4. Banking & Corporate Security Constraints

When operating inside a restricted banking environment:
- **Zero Secrets**: Never embed credentials, tokens, connection strings, or private keys in code or prompts.
- **Sanitization & Validation**: All external inputs must be validated against a strict allowlist.
- **Defensive Logging**: Never log Personally Identifiable Information (PII), payment card information (PCI), or sensitive financial data.
- **Fail Closed**: In security or error-handling flows, systems must fail closed (deny by default).
- **Auditability**: Maintain full traceability of requirements, changes, and verification receipts.
