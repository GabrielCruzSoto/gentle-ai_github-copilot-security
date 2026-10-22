---
name: chained-pr
description: "Split oversized changes (>400 lines) into chained/stacked PRs that protect review focus. Trigger: large features, stacked branches."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Chained Pull Requests Skill

## When to Use

Load this skill when a feature's scope or file forecast exceeds the 400-line budget, or when a large architectural migration must be delivered incrementally without breaking `main`.

## Hard Rules

1. **Slice by Domain Boundary, Not by Layer**:
   - Do not slice purely by horizontal layers (e.g. PR 1: all DB models, PR 2: all services, PR 3: all controllers).
   - Slice vertically by end-to-end usable sub-capabilities whenever possible, or by stable underlying contract followed by consumer implementation.
2. **Reviewable in ≤ 45 Minutes**:
   - Each PR in the chain must be small enough for a human reviewer to inspect with full mental focus in under 45 minutes.
3. **Explicit Dependency Mapping**:
   - Each chained PR must document its parent and child branches in its description:
     ```
     [Parent PR #101] ➔ [Current PR #102 📍] ➔ [Next PR #103]
     ```
4. **Target Branching**:
   - PR #1 targets `main`.
   - PR #2 targets branch #1.
   - When PR #1 merges, rebase/retarget PR #2 to `main`.
