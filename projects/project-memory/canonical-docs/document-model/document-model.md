---
date: 2026-03-14
project: project-memory
topic: document-model
registry_scope: document-model
source: agent
status: active
---
# Canonical Doc

## Summary

The managed data model is based on project-scoped Markdown documents with validated frontmatter, stable path rules, typed document roles, and explicit lifecycle semantics rather than ad hoc repository files or implicit conventions.

## Guidance

- Use managed document types with stable repository paths: session-note, verification-result, provider-note, decision, runbook, canonical-doc, and work-item.
- Treat frontmatter and body structure as validated contract surfaces rather than informal formatting; path layout, metadata, and required sections are part of the tool behavior.
- Store canonical docs under canonical-docs/<registry_scope>/<topic>.md and use registry_scope as the declared authority boundary for that canonical surface.
- Keep document lifecycle semantics explicit: document status controls managed visibility, while work-item execution progress is represented separately through work_item_state.
- Do not overload decisions as executable backlog items; long-lived rationale, current truth, operational guidance, and executable work must remain distinct document roles.

## References

- decision: canonical-doc-minimal-shape
- decision: decision-and-work-item-separation
- decision: work-item-schema-and-lifecycle-model
- decision: topic-and-scope-registry
- runbook: taxonomy-registry-baseline
- runbook: document-lifecycle-graph-baseline
