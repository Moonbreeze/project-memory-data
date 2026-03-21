---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: fail-soft-backlog-reads-on-invalid-work-items
source: agent
status: archived
work_item_state: done
---
# Work Item

## Summary

Fix mass-read backlog/list UX so invalid work-item documents are reported as diagnostics instead of aborting the entire read surface.

## Outcome

Project-memory has a tracked implementation slice for making backlog and list retrieval fail soft around invalid managed documents, so callers still receive usable planning output plus explicit diagnostics about skipped invalid records.

## Provenance

- ad-hoc: Follow-up to the recent work-item validation tightening: after adding the done-state session-note evidence invariant, reading the backlog exposed a UX bug where invalid active work-items abort mass-read surfaces instead of being surfaced as diagnostics.

## Dependencies

- work-item:project-memory:2026-03-21:clarify-work-item-closure-and-evidence-flow

## Context

- none

## Verification

- Verify read_planning_backlog returns usable backlog results when unrelated invalid active work-items exist and reports explicit diagnostics for the skipped documents.
- Verify list_documents backlog-style work-item reads no longer fail the whole response because of invalid work-items outside the returned selection and expose the invalid-document diagnostics to callers.
- Verify the strict validation invariant still applies to writes and direct document reads; only mass-read aggregation paths should degrade gracefully.
- Verify regression tests cover the bug through the core read surface and MCP-facing result shape, with the bug registered in the project test bug registry.

## Evidence

- session-note:project-memory:2026-03-21:fail-soft-backlog-reads-on-invalid-work-items
- verification-result:project-memory:2026-03-21:fail-soft-backlog-reads-on-invalid-work-items
