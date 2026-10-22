# Organic Driven Development (ODD) Workflow Manual

## 1. What is ODD?

**Organic Driven Development (ODD)** is a deterministic engineering workflow designed to prevent AI-generated architectural rot, uncontrolled scope creep, and unverified assumptions.

In standard AI-assisted coding, models jump straight into generating speculative code, accumulating tech debt and hallucinated fixes. ODD forces a disciplined rhythm:

```
Spec First ➔ Strict TDD ➔ 4R Review & Receipts ➔ Atomic Work Unit
```

---

## 2. Phase-by-Phase Execution

### Phase 1: Specification & GitFlow Branching (`odd/tasks/<feature>.md`)
1. Create a new task file from `odd/TEMPLATE.md`.
2. Create the corresponding GitFlow branch:
   - For new features: `git checkout -b feature/<task-id>-<slug> develop`
   - For production incidents: `git checkout -b hotfix/<incident-id>-<slug> main`
3. Define the exact boundary of what is in scope and what is explicitly out of scope.
4. List acceptance criteria, including negative controls (failure cases, invalid inputs).
5. Estimate total changed lines (budget: ≤ 400 lines).

### Phase 2: Strict Test-Driven Development (TDD)
1. **Red**: Write a test asserting the single next behavior.
2. **Green**: Write the minimal code to satisfy the assertion.
3. **Refactor**: Clean up the design while keeping tests green.
4. Update the task checklist in `odd/tasks/<feature>.md`.

### Phase 3: Evidence & 4R Review (`odd/evidence/<feature>.md`)
1. Execute the 4R review lens (`/review-4r`).
2. Document all findings in the evidence ledger.
3. If any findings are rated `BLOCKER` or `CRITICAL`, run the adversarial refuter (`/review-refuter`).
4. Resolve all confirmed blockers before proceeding.

### Phase 4: Atomic Work Unit Commit & GitFlow Pull Request
1. Ensure tests and docs are staged with the code on the `feature/*` branch.
2. Confirm the line count is under 400 lines.
3. Use `/work-unit-commit` to format a standard Conventional Commit.
4. Record the final receipts in the task file and mark the task as `completed`.
5. Open a Pull Request targeting `develop` (or `main` + `develop` for a hotfix). See [GitFlow Guide](gitflow-workflow.md).
