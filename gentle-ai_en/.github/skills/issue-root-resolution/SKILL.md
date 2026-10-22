---
name: issue-root-resolution
description: "Isolate, reproduce, and resolve root causes of defects. Trigger: bug fixes, regression investigations, incident post-mortems."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Issue Root Resolution Skill

## When to Use

Load this skill when investigating a bug, error trace, or production incident.

## Resolution Protocol

1. **Reproduction Before Fix**:
   - Never write code attempting to fix a bug without first reproducing it with a deterministic, failing test.
   - If reproduction cannot be automated in a unit test, formulate a minimal reproducible script or harness.
2. **5-Whys Root Cause Analysis**:
   - Distinguish the symptom (e.g. `NullPointerException`, unexpected HTTP 500) from the structural cause (e.g. unhandled concurrency state, invalid schema deserialization, race condition).
3. **Surgical Fix with Invariant Protection**:
   - Fix the vulnerability at the root. Do not wrap symptoms with defensive null checks that hide corrupted state.
   - Verify that fixing the bug does not introduce regressions across adjacent modules.
4. **Receipt Documentation**:
   - Record the root cause, failing test receipt, and fix rationale in `odd/evidence/<issue-id>-resolution.md`.
