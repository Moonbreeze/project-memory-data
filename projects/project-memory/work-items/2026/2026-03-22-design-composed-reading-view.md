---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: design-composed-reading-view
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define the composition model for a continuous reading view over bounded document packages.

## Outcome

Project-memory has an explicit design for a composed reading projection that merges selected managed document bodies into one continuous reading flow while preserving provenance, authority boundaries, and deterministic ordering.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline

## Context

- canonical-doc:project-memory:document-model:document-model
- canonical-doc:project-memory:reads:bounded-read-model

## Verification

- Define the initial composition modes and include at least topic, rationale, and cold-start projections unless a narrower scope is explicitly justified.
- Specify ordering semantics for composed blocks and how they relate to bounded-read stages.
- Preserve provenance and authority markers without forcing full metadata chrome on every block.
- Define hover or click interactions for revealing path, status, type, date, and original document boundaries.
- Explain why composed reading remains a projection over stored documents rather than becoming a new summary authority surface.

## Evidence

- none
