---
date: 2026-03-15
project: project-memory
topic: intra-day-document-ordering-and-timeline-model
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Define and implement a timeline model for ordering managed documents within the same day.

## Outcome

Project-memory can answer newest-within-day questions and support a stable human-readable timeline without relying on filesystem metadata or path-name accidents.

## Provenance

- ad-hoc: Documentation and architecture review identified that current ordering is date-first with path tie-breaks only, which is insufficient for true same-day timelines and future human-facing views.

## Dependencies

- none

## Context

- decision:project-memory:2026-03-17:document-timeline-and-latest-first-query-defaults

## Verification

- Document the current ordering behavior and its limitations.
- Decide what timestamp or ordering field should become part of the managed model.
- Define how list, bounded reads, and future human-facing timeline views should use the new ordering semantics.

## Evidence

- session-note:project-memory:2026-03-17:document-timeline-implementation
- verification-result:project-memory:2026-03-17:document-timeline-and-latest-first-query-defaults
