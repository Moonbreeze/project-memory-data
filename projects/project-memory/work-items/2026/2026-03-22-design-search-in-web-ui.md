---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: design-search-in-web-ui
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define the search UX and contract for the Web UI over existing shared-core search behavior.

## Outcome

Project-memory has an explicit search design for the Web UI, including query and route semantics, ordering expectations, excerpt behavior, and the boundary between the existing substring-search core and any later UX shaping.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline

## Context

- canonical-doc:project-memory:document-model:document-model
- canonical-doc:project-memory:reads:bounded-read-model
- decision:project-memory:2026-03-17:document-timeline-and-latest-first-query-defaults

## Verification

- Decide whether Web search initially wraps the current substring-search core unchanged or adds extra shaping on top.
- Define search ordering semantics and their relation to the latest-first defaults already used elsewhere.
- Define search-result excerpt behavior and any initial match-highlighting expectations.
- Define route and query-parameter semantics for shareable search URLs.
- Explain why search remains outside the baseline v1 scope even though shared-core search support already exists.

## Evidence

- none
