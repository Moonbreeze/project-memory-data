---
date: 2026-03-15
project: project-memory
topic: draft-decision-idea-inbox-and-triage-model
source: user
status: active
---
# Decision

## Context

The current model already separates executable planning from decisions: project-scoped backlog views prefer work items, while legacy decision-backed backlog behavior remains only as a fallback. A frequent missing workflow is how to capture early project ideas that are worth remembering but have not yet been discussed enough to become accepted policy or executable work. Without an explicit model, those ideas either get mixed into backlog semantics or disappear into ad hoc notes.

## Decision

Treat draft decisions as the managed inbox for untriaged project ideas. Add an `ideas` list-documents preset that returns draft decisions ordered newest first and use it as the standard review surface for idea triage. Do not treat draft decisions as future work by themselves. When an idea is ready for active investigation, create a work item that references the draft decision. When triage completes, record a new active decision that captures either the accepted concept or the explicit rejection, rather than mutating the original draft decision into the final record.

## Consequences

- The model preserves the existing separation of concerns: decisions capture ideas and policy, while work items represent actual planning and execution work.
- Agents get a standard discovery surface for previously mentioned ideas without overloading the backlog preset with non-executable entries.
- Idea review can proceed incrementally: a draft decision can sit in the inbox until someone creates a work item for analysis, validation, or implementation planning.
- Historical traceability improves because the original draft idea, the triage work item, and the final active decision remain separate records with explicit links.
