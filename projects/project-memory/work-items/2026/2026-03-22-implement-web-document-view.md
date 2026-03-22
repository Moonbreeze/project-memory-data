---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: implement-web-document-view
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Build the exact managed-document page for the read-only Web UI.

## Outcome

The Web UI has an exact document route that renders one managed document with provenance metadata, a body container, and navigation back to browsing views while remaining strictly read-only.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline
- work-item:project-memory:2026-03-22:implement-web-runtime-shell
- work-item:project-memory:2026-03-22:implement-web-read-adapter

## Context

- canonical-doc:project-memory:document-model:document-model

## Verification

- Accept a stable document identifier and resolve it through shared core logic rather than through direct ad hoc file reads in the Web layer.
- Show provenance-relevant metadata, including type, project, topic, status, date, recorded_at, and relativePath.
- Render a body container and deterministic fallback behavior for missing or invalid documents.
- Provide navigation back to timeline or filter context where possible.
- Keep the page strictly read-only.

## Evidence

- none
