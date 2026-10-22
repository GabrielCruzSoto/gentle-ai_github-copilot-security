# GitFlow Workflow Guide for GitHub Copilot in Banking

## 1. Why GitFlow in Banking Environments?

In banking and financial institutions, production software demands **maximum stability, traceability, and auditable version control**.

GitFlow establishes a strict separation of concerns between active feature development, release stabilization, and verified production code:

- **Isolation**: Features under development never pollute production branches.
- **Regulatory Traceability**: Every release and hotfix carries an immutable semantic version tag (`vX.Y.Z`).
- **Access Control & Auditing**: The `main`, `master`, `prod`, and `develop` branches are protected; all changes enter via Pull Requests vetted by 4R reviews and test receipts.

---

## 2. GitFlow Branching Model

```
main        ──────────────────────────────● (v1.0.0)─────────● (v1.0.1)───────● (v1.1.0)
             \                           /                   /                 /
hotfix        \                         /       ●───────────● (hotfix/1.0.1)  /
               \                       /       /             \               /
develop         ●──────────●──────────●───────●───────────────●─────────────●
                 \        /            \                                   /
feature           ●──────● (feat/A)     \                                 /
                                         ●───────────────────────────────● (release/1.1.0)
```

### Main Branches (Permanent & Protected)

> [!CAUTION]
> **Total Prohibition of Direct Commits:**
> Direct commits or pushes to `prod`, `production`, `master`, `main`, or `develop` branches are strictly forbidden. All changes, without exception, must enter via a **Pull Request (PR)** validated by automated tests and approved through 4R review.

| Branch | Purpose | Rules |
|---|---|---|
| `main` / `master` / `prod` | Official production code | **ZERO DIRECT COMMITS**. Only receives merges from `release/*` and `hotfix/*` via Pull Request. Each merge creates a semantic tag (`vX.Y.Z`). |
| `develop` | Ongoing feature integration | **ZERO DIRECT COMMITS**. Starting point for `feature/*` and `release/*`. Receives merges from `feature/*` exclusively via Pull Request. |

---

## 3. Supporting Branches (Temporary)

### A. Feature Branches (`feature/*`)
- **Origin**: `develop`
- **PR Target**: `develop`
- **Naming**: `feature/<task-id>-<short-description>` (e.g. `feature/ODD-101-instant-transfers`)
- **Workflow**:
  1. Branch off `develop`: `git checkout -b feature/ODD-101-instant-transfers develop`
  2. Write feature spec in `odd/tasks/ODD-101-instant-transfers.md`.
  3. Implement with strict TDD and atomic commits under 400 lines.
  4. Perform 4R review sweep (`/review-4r`) and adversarial refutation if blockers exist.
  5. Open Pull Request targeting `develop`.

### B. Release Stabilization Branches (`release/*`)
- **Origin**: `develop`
- **PR Target**: `main` **AND** `develop`
- **Naming**: `release/v<X.Y.Z>` (e.g. `release/v1.2.0`)
- **Workflow**:
  1. Branch off `develop` when all cycle features are complete.
  2. Only minor bug fixes, documentation polishes, and final banking security audits (`/banking-security`) are permitted.
  3. Upon approval:
     - Merge into `main` and tag `v1.2.0`.
     - Merge back into `develop` to sync stabilization fixes.
  4. Delete the release branch.

### C. Production Hotfix Branches (`hotfix/*`)
- **Origin**: `main`
- **PR Target**: `main` **AND** `develop`
- **Naming**: `hotfix/<incident-id>-<short-description>` (e.g. `hotfix/INC-901-fix-gateway-timeout`)
- **Workflow**:
  1. Branch directly from affected production tag: `git checkout -b hotfix/INC-901 main`
  2. Apply fix via strict TDD (reproduce with failing test first).
  3. Run focused 4R review (R1 Risk and R4 Resilience).
  4. Upon approval:
     - Merge into `main` and tag patch release (e.g. `v1.2.1`).
     - Merge back into `develop` to prevent regression.
  5. Delete the hotfix branch.

---

## 4. Integration with ODD and GitHub Copilot

1. **Before Coding**: Prompts `/orchestrator` and `/odd-spec` verify that the active branch matches the `feature/*` or `hotfix/*` convention.
2. **During Coding**: Commits formatted by `/work-unit-commit` are made exclusively on the supporting branch without touching `develop` or `main`.
3. **Before PR**: Skill `branch-pr` verifies the target branch (`develop` for features, `main` + `develop` for releases/hotfixes) and test receipts.
