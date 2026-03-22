---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: design-graph-view-edge-model
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define the supported node and edge model for a Web graph view over managed documents.

## Outcome

Project-memory has an explicit graph-view model that defines supported nodes, supported edge types, excluded inferred links, and display guardrails so the graph does not imply stronger semantics than the stored documents actually provide.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:design-read-only-web-interface-baseline

## Context

- canonical-doc:project-memory:document-model:document-model
- canonical-doc:project-memory:work-item-planning:work-item-planning-model

## Verification

- Enumerate the initial node types and edge types sourced from existing managed relationships.
- Distinguish authoritative, navigational, and derived edges rather than treating every link as semantically equal.
- Define which inferred links are explicitly excluded from the first graph behavior.
- Define graph-navigation expectations back to exact document view.
- Explain how the graph avoids implying stronger authority than the stored documents provide.

## Evidence

- none
