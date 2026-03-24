---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: implement-web-timeline-view
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Build the latest-first timeline page for the read-only Web UI.

## Outcome

The Web UI has a main timeline page that lists managed documents in the existing latest-first order, exposes entry metadata needed for browsing, and links into exact document views without introducing any write affordances.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline
- work-item:project-memory:2026-03-22:implement-web-runtime-shell
- work-item:project-memory:2026-03-22:implement-web-read-adapter

## Context

- canonical-doc:project-memory:document-model:document-model
- decision:project-memory:2026-03-17:document-timeline-and-latest-first-query-defaults

## Verification

- Render a timeline page whose ordering matches the existing latest-first date, recorded_at, and relativePath semantics.
- Show the core browsing metadata for each entry, including type, project, topic, status, date, and relativePath or its stable route equivalent.
- Link each timeline entry into the exact document view.
- Avoid duplicating list-query ordering rules in the Web layer.
- Keep the page strictly read-only.

## Evidence

- session-note:project-memory:2026-03-24:implement-web-timeline-view
- verification-result:project-memory:2026-03-24:implement-web-timeline-view
