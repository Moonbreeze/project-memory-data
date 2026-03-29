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

Design and implement the MVP domain model for routine-pack orchestration and built-in runtime action references.

## Outcome

Waypoint has a minimal but coherent routine-pack domain model that captures the agreed orchestration boundaries: routines, pack-level model routing, selective ai-inst instruction loadouts, execution-shape and delegation semantics, deterministic hook references, and typed references to built-in runtime system actions. The model is concrete enough to validate an example pack without yet requiring a fully featured coordinator runtime.

## Provenance

- decision:waypoint:2026-03-29:routine-pack-orchestration

## Dependencies

- none

## Context

- session-note:waypoint:2026-03-29:routine-pack-architecture-exploration
- decision:waypoint:2026-03-29:routine-pack-orchestration

## Verification

- A representative routine-pack example can be expressed and validated with the MVP schema or TypeScript model.
- The model separates logical execution shape from delegation rights instead of collapsing both concerns into one ambiguous mode field.
- Routine hooks and runtime steps reference typed built-in system actions or other routines rather than embedding arbitrary shell command strings.
- Routine model selection uses workload classes while concrete provider/model mapping lives at the pack-routing layer.

## Evidence

- none
