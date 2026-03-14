---
date: 2026-03-14
project: project-memory
topic: work-item-origins-and-provenance
source: user
status: active
---
# Decision

## Context

The future work-item model needs to represent both planned implementation derived from existing decisions or follow-ups and ad hoc operational work that emerges from bugs, code review, tests, or direct user requests. Requiring a pre-existing decision or session note for every work item would create artificial paperwork, but allowing originless tasks would weaken traceability.

## Decision

Allow work items to originate from decisions, follow-ups, or ad hoc discovery. Require every work item to carry minimal provenance, including an origin type and enough source context to explain why the item exists, while reserving richer evidence such as session notes, verification results, decision updates, or canonical-doc edits for the work completion and behavior-change stages.

## Consequences

- Ad hoc work can enter the backlog without forcing a synthetic decision or session note first.
- The future work-item schema should include explicit origin metadata such as origin_type and origin_summary or equivalent linked-source fields.
- Completing a work item that changes behavior or process should still produce the appropriate downstream records: session notes, verification results, and canonical-doc or decision updates when needed.
- Backlog quality depends on provenance completeness rather than on an inflexible requirement that every task be predeclared in another document type.
