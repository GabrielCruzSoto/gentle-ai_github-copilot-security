# ODD Feature Specification: <Feature Name>

- **Status**: `draft` | `in-progress` | `in-review` | `completed`
- **Owner**: <Developer / Pair>
- **Target Line Budget**: ≤ 400 changed lines
- **Parent Ticket / Issue**: #<Issue-ID>
- **GitFlow Branch**: `feature/<task-id>-<slug>` (Base: `develop`, PR Target: `develop`)

---

## 1. Intent & Business Value

### What problem are we solving?
A concise description of the functional or architectural need.

### Out of Scope (Non-Goals)
Explicitly list what will NOT be addressed in this work unit.

---

## 2. Architectural Design & Impact

### Component / Module Boundaries
- **Modified Interfaces / Types**:
- **New Files**:
- **Public Contract Changes**:

### Banking Security Checklist
- [ ] No PII/PCI leaked to logs or exceptions
- [ ] Safe monetary math (no floating point)
- [ ] Fail-closed authorization and validation
- [ ] Idempotency addressed if mutation

---

## 3. Acceptance Criteria & Negative Controls

### Happy Path Expectations
1. Given `<context>`, when `<action>`, then `<expected result>`.

### Negative Control & Edge Cases
1. Given `<invalid/empty input>`, when `<action>`, then `<expected error / rejection>`.
2. Given `<timeout / upstream failure>`, when `<action>`, then `<graceful degradation>`.

---

## 4. Execution Tasks (Strict TDD)

- [ ] **Step 1 (Test First)**: Add failing behavioral test in `test/<module>.test.ts`
- [ ] **Step 2 (Implementation)**: Minimal implementation in `src/<module>.ts`
- [ ] **Step 3 (Refactor & Types)**: Clean up and strengthen interfaces
- [ ] **Step 4 (Review)**: Run 4R review sweep (`/review-4r`) and log receipts
- [ ] **Step 5 (Commit)**: Conventional commit (≤ 400 lines)

---

## 5. Verification Receipts & Evidence

Link to the evidence ledger: `odd/evidence/<feature>-receipts.md`

- **Test Suite Command**: `npm test` / `pytest` / `go test ./...`
- **Result**: `Passed (X tests, 0 failures)`
- **Review Ledger**: `R1: Clean | R2: Clean | R3: Clean | R4: Clean`
