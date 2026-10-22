---
name: cognitive-doc-design
description: "Design documentation that minimizes cognitive load. Trigger: writing guides, READMEs, RFCs, architecture specs."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Cognitive Doc Design Skill

## When to Use

Load this skill when writing or editing technical documentation, PR descriptions, architecture guides, or task specifications.

## Core Patterns

1. **Lead with the Decision / Answer**:
   - State the outcome, recommendation, or essential command first. Put background context and historical evolution second.
2. **Tables over Walls of Text**:
   - Use structured Markdown tables for component maps, configurations, and tradeoffs.
3. **Mermaid Diagrams for Architecture**:
   - Prefer concise Mermaid flowcharts or sequence diagrams over multi-paragraph descriptions of call stacks or data flows.
4. **Scannable Hierarchy**:
   - Use bold lead-ins for list items.
   - Keep paragraphs under 3-4 sentences.
   - Use code fences with explicit language identifiers.
