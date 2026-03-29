---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: design-search-in-web-ui
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Define the on-demand Web search UX, route contract, and collapsible-control expectations for the read-only Web UI.

## Outcome

Project-memory has an explicit search design for the Web UI, including a dedicated `/search` route, the shareable `q`/`project`/`type`/`limit` query contract, latest-first ordering and excerpt expectations inherited from shared core, on-demand entry from the timeline shell, and reusable collapsible-control guidance for compact search and filter surfaces.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline

## Context

- canonical-doc:project-memory:document-model:document-model
- canonical-doc:project-memory:reads:bounded-read-model
- canonical-doc:project-memory:web-ui:read-only-web-ui-guidance
- decision:project-memory:2026-03-17:document-timeline-and-latest-first-query-defaults
- decision:project-memory:2026-03-29:web-search-route-and-collapsible-control-pattern

## Verification

- Decide whether Web search initially wraps the current shared-core substring-search behavior unchanged or adds extra shaping on top.
- Define search ordering semantics and keep them aligned with the latest-first defaults already used elsewhere.
- Define search-result excerpt behavior and explicitly defer initial match-highlighting or Web-only ranking semantics.
- Define route and query-parameter semantics for shareable search URLs, including why v1 does not add a Web-only `status` filter.
- Define how search stays on-demand from the timeline shell and how the `/search` view uses collapsible controls without permanently expanding the form.
- Explain why search remains outside the baseline v1 scope even though shared-core search support already exists.

## Evidence

- session-note:project-memory:2026-03-29:web-search-design-and-web-ui-guidance-audit
- verification-result:project-memory:2026-03-29:design-search-in-web-ui
