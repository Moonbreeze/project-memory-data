---
date: 2026-03-29
recorded_at: 2026-03-29T10:38:45.104Z
project: waypoint
topic: routine-pack-domain-model-mvp
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Design and implement the MVP domain model for routine-pack orchestration and built-in runtime action references, with explicit support for later authoring and validation surfaces.

## Outcome

Waypoint has a minimal but coherent routine-pack domain model that captures the agreed orchestration boundaries: routines, pack-level model routing, selective ai-inst instruction loadouts, execution-shape and delegation semantics, deterministic hook references, typed references to built-in runtime system actions, and enough structure to back a dedicated authoring and validation surface. The model is concrete enough to validate and preview a representative pack without yet requiring a fully featured coordinator runtime or finished UI.

## Provenance

- decision:waypoint:2026-03-29:routine-pack-orchestration

## Dependencies

- work-item:waypoint:2026-03-29:routine-pack-authoring-surface-definition

## Context

- session-note:waypoint:2026-03-29:routine-pack-architecture-exploration
- decision:waypoint:2026-03-29:routine-pack-orchestration
- decision:waypoint:2026-03-29:routine-pack-authoring-surfaces

## Verification

- A representative routine-pack example can be expressed, validated, and previewed with the MVP schema or TypeScript model.
- The model separates logical execution shape from delegation rights instead of collapsing both concerns into one ambiguous mode field.
- Routine hooks and runtime steps reference typed built-in system actions or other routines rather than embedding arbitrary shell command strings.
- Routine model selection uses workload classes while concrete provider/model mapping lives at the pack-routing layer.
- The model is structured so a dedicated authoring surface can inspect, edit, validate, and preview routines and packs without transport-specific assumptions.

## Evidence

- none
