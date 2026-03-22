---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: implement-composed-reading-view
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Implement the composed reading screen for continuous reading across bounded document packages.

## Outcome

The Web UI supports a composed reading screen that merges selected managed document bodies into one continuous reading flow while preserving deterministic ordering, subtle document boundaries, and expandable provenance details.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-composed-reading-view
- work-item:project-memory:2026-03-22:implement-web-runtime-shell
- work-item:project-memory:2026-03-22:implement-web-read-adapter
- work-item:project-memory:2026-03-22:implement-web-document-view
- work-item:project-memory:2026-03-22:implement-web-markdown-rendering

## Context

- canonical-doc:project-memory:reads:bounded-read-model
- canonical-doc:project-memory:document-model:document-model

## Verification

- Render multiple documents as one continuous reading flow with subtle but visible document boundaries.
- Allow users to reveal original document details without leaving the reading surface.
- Keep ordering and document selection aligned with the approved composition model.
- Reuse existing document rendering and Web adapter logic instead of duplicating formatting or retrieval rules.
- Make it explicit that the composed reading screen is a projection, not a new canonical document.

## Evidence

- none
