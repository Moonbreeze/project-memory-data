---
date: 2026-03-15
recorded_at: 2026-03-15T00:00:00.000Z
project: project-memory
topic: implement-ideas-preset-and-idea-triage-flow
source: user
status: archived
work_item_state: done
---
# Work Item

## Summary

Implement the new idea-intake retrieval surface so draft decisions can be reviewed as an inbox without polluting backlog semantics.

## Outcome

Project-memory exposes an `ideas` preset for draft decisions, documents the idea-to-triage lifecycle, and verifies the behavior with automated tests.

## Provenance

- decision:project-memory:2026-03-15:draft-decision-idea-inbox-and-triage-model

## Dependencies

- none

## Context

- decision:project-memory:2026-03-15:draft-decision-idea-inbox-and-triage-model
- decision:project-memory:2026-03-14:work-item-backlog-fallback-policy
- decision:project-memory:2026-03-14:work-item-schema-and-lifecycle-model

## Verification

- Add automated coverage for `list-documents --preset ideas`, including filtering to draft decisions and newest-first ordering.
- Update CLI/MCP-visible preset definitions and docs so the `ideas` surface is discoverable and semantically distinct from backlog.
- Confirm the implementation preserves existing backlog behavior and does not reclassify draft decisions as executable work items.

## Evidence

- session-note:project-memory:2026-03-16:implement-ideas-preset-and-idea-triage-flow
- verification-result:project-memory:2026-03-16:implement-ideas-preset-and-idea-triage-flow
