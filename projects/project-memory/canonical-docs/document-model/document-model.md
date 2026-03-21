---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: document-model
registry_scope: document-model
source: agent
status: active
---
# Canonical Doc

## Summary

The managed data model is based on project-scoped Markdown documents with validated frontmatter, stable path rules, typed document roles, explicit lifecycle semantics, declared authority boundaries, explicit decision-write review semantics, and explicit timeline semantics for chronological ordering.

## Guidance

- Use managed document types with stable repository paths: session-note, verification-result, provider-note, decision, runbook, canonical-doc, and work-item.
- Treat frontmatter and body structure as validated contract surfaces rather than informal formatting; path layout, metadata, and required sections are part of the tool behavior.
- Store canonical docs under canonical-docs/<registry_scope>/<topic>.md and use registry_scope as the declared authority boundary for that canonical surface.
- Keep document lifecycle semantics explicit: document status controls managed visibility, while work-item execution progress is represented separately through work_item_state.
- Archive semantics depend on document type: session notes and verification results archive by moving into archives/, while provider notes, decisions, runbooks, canonical docs, and work items archive in place by status unless a type-specific lifecycle rule says otherwise.
- Reserve runbooks for repeatable operational procedures. Baseline model guidance or policy belongs in canonical docs or decisions, while transient planning or discovery artifacts belong in work items, session notes, or archives rather than in active runbooks.
- Preserve one authoritative active canonical doc per declared scope; if two documents claim the same authority boundary, treat that as a modeling error and resolve it by narrowing scope, splitting content, or superseding the older document.
- Allow partial migration between repository docs and project-memory canonical docs only when each topic scope clearly declares where current authority lives.
- Use canonical-doc status intentionally: mark a canonical doc superseded when a newer authoritative doc replaces it for the same scope, and use archived only when the scope is retired or intentionally removed from the active corpus.
- Archive work items only after they reach done or canceled and no longer belong in active planning; do not use archival as the normal moment of completion.
- Treat cross-project references as explicit links, not as implicit authority transfer or default read widening.
- Do not overload decisions as executable backlog items; long-lived rationale, current truth, operational guidance, and executable work must remain distinct document roles.
- Use `recorded_at` as the managed timeline key for intra-day chronology while keeping `date` as the day-level bucket and path key.
- When a stored document lacks explicit `recorded_at`, use a deterministic fallback derived from `date` rather than filesystem metadata or path-name accidents.
- Treat timeline-aware chronological ordering as `date`, then `recorded_at`, then `relativePath`, with descending order meaning newest-first and ascending order meaning oldest-first.
- Require non-draft decision writes to record an explicit stable-guidance review outcome, while draft decisions remain the lightweight idea-inbox form.
- Use explicit review outcomes to distinguish reviewed-no-change, update-required, updated, and bootstrap-exempt decision writes rather than leaving stable-guidance handling implicit.
- Treat each decision path as an immutable durable record; create a new decision or apply lifecycle semantics such as supersession instead of overwriting an existing dated decision path.

## References

- decision: canonical-doc-minimal-shape
- decision: decision-and-work-item-separation
- decision: work-item-schema-and-lifecycle-model
- decision: topic-and-scope-registry
- decision: taxonomy-registry-baseline
- decision: decision-write-guidance-review-contract
- decision: document-timeline-and-latest-first-query-defaults
- canonical-doc: taxonomy-registry
