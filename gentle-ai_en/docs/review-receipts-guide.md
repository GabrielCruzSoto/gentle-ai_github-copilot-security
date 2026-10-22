# 4R Review & Verification Receipts Guide

## 1. Principles of Receipt-Driven Review

In high-stakes enterprise and financial software, a code review must produce **falsifiable evidence**, not subjective opinions or superficial thumbs-up reactions.

Every change undergoes a structured review across four orthogonal lenses (the **4R Model**):

```
       ┌────────────────────────┐
       │       Diff / PR        │
       └───────────┬────────────┘
                   │
    ┌──────────────┼──────────────┬──────────────┐
    ▼              ▼              ▼              ▼
[R1: Risk]   [R2: Readability] [R3: Reliability] [R4: Resilience]
    │              │              │              │
    └──────────────┴──────┬───────┴──────────────┘
                          ▼
            [Unified Findings Ledger]
                          │
                   (Blockers?)
                  Yes /       \ No
                     /         \
        [Adversarial Refuter]   [Clean Receipt]
```

---

## 2. The 4 Lenses

| Lens | Focus Areas | Key Failure Modes |
|---|---|---|
| **R1: Risk** | Security, OWASP, PII/PCI, authentication, authorization | Leaking secrets, SQL injection, missing tenant check |
| **R2: Readability** | Cognitive load, naming, encapsulation, clean architecture | Spaghetti logic, deep nesting, misleading names |
| **R3: Reliability** | Behavioral tests, determinism, edge cases, contracts | Untested behavior, race condition, missing null check |
| **R4: Resilience** | Resource leaks, timeouts, fallbacks, fail-safe defaults | Unclosed handles, hanging requests, cascading crash |

---

## 3. Severity Levels & Adversarial Verification

- **BLOCKER**: Immediate safety, security, or data-integrity hazard. Merging is forbidden until resolved or refuted.
- **CRITICAL**: Significant functional defect or missing contract test.
- **WARNING**: Architectural smell or edge-case weakness that does not break core invariant.
- **SUGGESTION**: Optional improvement or future optimization.

### The Adversarial Refuter
To prevent false-positive paralysis from AI reviewers, any `BLOCKER` or `CRITICAL` finding can be challenged by the **Review Refuter** (`/review-refuter`).
- The Refuter searches for concrete evidence (e.g. existing upstream middleware, defensive type guarantees, existing tests) that proves the finding is invalid.
- If refuted with proof, the finding is marked `Refuted` in the ledger and does not block delivery.
