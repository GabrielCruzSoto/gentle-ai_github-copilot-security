---
name: systemic-issue-triage
description: "Triage defect backlogs by root classes rather than individual symptoms. Trigger: bug triage, backlog grooming, defect clustering."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Systemic Issue Triage Skill

## When to Use

Load this skill when triaging incoming bug reports or managing a defect backlog. The goal is to prevent symptom patching and avoid architectural bloat.

## Hard Rules

1. **Cluster by Structural Invariant**:
   - Do not fix 10 similar bugs with 10 separate patches.
   - Group defects by the underlying architectural invariant that failed (e.g. session lifecycle, currency rounding, authorization header propagation).
2. **One Root Fix Closes the Cluster**:
   - Design a single structural correction that closes the entire cluster of symptoms.
   - Write automated tests proving every symptom in the cluster is eradicated.
3. **Classification Taxonomy**:
   - `Superceded`: Bug rendered obsolete by upcoming design changes.
   - `Duplicate`: Belongs to an existing tracked cluster.
   - `Systemic Defect`: Real bug belonging to a structural invariant failure.
   - `Incomplete`: Insufficient details from reporter; clarify before coding.
