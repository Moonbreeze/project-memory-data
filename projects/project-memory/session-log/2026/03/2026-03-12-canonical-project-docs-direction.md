---
date: 2026-03-12
project: project-memory
topic: canonical-project-docs-direction
source: user
status: active
---
# Session Note

## Summary

Recorded the decision and implementation direction for expanding project-memory so it can become the canonical home for full project documentation when a consumer project wants that model.

## Actions

- Evaluated the current project-memory model and confirmed it only supports session notes, verification results, provider notes, decisions, and runbooks.
- Identified the main missing capability: a first-class canonical project-document type with update or upsert semantics and a less rigid documentation validator.
- Recorded a decision that full project-doc externalization into project-memory should be supported explicitly, not by overloading existing document kinds.
- Recorded that the ai-inst project-memory rules module should gain a conditional clarification telling agents to look for explicit project-specific policy before assuming repo docs can be replaced by project-memory.

## Follow-up

- Add the canonical document type and write path in project-memory.
- Update the ai-inst project-memory module text with the conditional project-policy clarification.
- When implementation exists, test the migration on a real consumer project that wants private documentation outside the tool repository.
