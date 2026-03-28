---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: implement-web-navigation-and-states
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Add cohesive navigation and fallback states across the Web UI.

## Outcome

The read-only Web UI has clear navigation between timeline and document pages plus deterministic empty, not-found, invalid-document, and configuration-error states instead of silent failures or dead ends.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:implement-web-timeline-view
- work-item:project-memory:2026-03-22:implement-web-document-view

## Context

- canonical-doc:project-memory:reads:bounded-read-model

## Verification

- Connect timeline and exact document views with explicit navigation affordances.
- Provide deterministic empty, not-found, invalid-document, and configuration-error states for list and document routes.
- Make current location and active filter context visible in the UI where relevant.
- Ensure routes fail predictably when PROJECT_MEMORY_ROOT or the requested document is invalid.
- Keep all navigation flows strictly read-only with no accidental write affordances.

## Evidence

- session-note:project-memory:2026-03-28:implement-web-navigation-and-states
- verification-result:project-memory:2026-03-28:implement-web-navigation-and-states
