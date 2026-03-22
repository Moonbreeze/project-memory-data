---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: design-read-only-web-interface-baseline
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Define the delivery architecture, first-version scope, and planned follow-up decomposition for a read-only Web UI over project-memory managed documents.

## Outcome

Project-memory has an explicit baseline design for a human-facing read-only Web UI, including the chosen runtime shape, shared-core data flow, v1 feature boundary, configuration model, explicit follow-up boundaries for search/composed/graph features, and the next implementation slices that can proceed without reopening the architecture.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- none

## Context

- decision:project-memory:2026-03-17:document-timeline-and-latest-first-query-defaults
- canonical-doc:project-memory:document-model:document-model
- canonical-doc:project-memory:work-item-planning:work-item-planning-model
- canonical-doc:project-memory:reads:bounded-read-model

## Verification

- Select one recommended delivery shape for v1 and explain why the rejected alternatives are not the baseline path.
- Define the UI data flow so the Web surface remains a read-only projection over the existing shared core and managed filesystem rather than a parallel source of truth.
- Fix the v1 feature boundary explicitly: timeline view, project filter, document-type filter, exact document view, and markdown rendering.
- Record search, composed reading view, and graph view as explicit follow-up scopes rather than leaving them ambiguous.
- Define how the Web UI receives PROJECT_MEMORY_ROOT and what local runtime or deployment assumptions it makes.
- Confirm that the chosen design works with the current recorded_at and latest-first timeline semantics without requiring document-model changes.
- Name the expected next implementation slices so backlog decomposition can proceed without reopening the baseline.

## Evidence

- session-note:project-memory:2026-03-22:read-only-web-interface-baseline
