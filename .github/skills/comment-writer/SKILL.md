---
name: comment-writer
description: "Write direct, respectful, technically grounded code and PR review comments. Trigger: code comments, review feedback."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Comment Writer Skill

## When to Use

Load this skill when authoring code comments, PR review feedback, or issue discussions.

## Principles

1. **In-Code Comments**:
   - Explain **WHY**, never WHAT. The code states what is happening; comments justify non-obvious business logic, bank regulatory constraints, or algorithmic subtleties.
   - Maintain comment integrity: if modifying code, update or delete outdated comments immediately.
2. **Review Feedback**:
   - Provide concrete technical reasoning and specific line references.
   - Separate objective defects (bugs, security risks, contract violations) from subjective style suggestions.
   - Always suggest a concrete alternative or patch when flagging a problem.
