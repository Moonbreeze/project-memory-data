---
date: 2026-03-29
recorded_at: 2026-03-29T10:49:25.057Z
project: waypoint
topic: routine-pack-authoring-surface-definition
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Define the MVP authoring UX and provider-neutral API boundary for creating, editing, validating, previewing, and publishing routines and routine packs.

## Outcome

Waypoint has a concrete authoring-surface definition for routine-pack work: Telegram is scoped to operational session handling, while a dedicated Web UI is scoped to human authoring and configuration. The project also has an explicit provider-neutral API and domain boundary for routine-pack drafts, validation, preview, inspection, diffing, and publish flows, so later UI work can build on a coherent backend contract instead of inventing transport-specific behavior.

## Provenance

- decision:waypoint:2026-03-29:routine-pack-authoring-surfaces

## Dependencies

- none

## Context

- decision:waypoint:2026-03-29:routine-pack-orchestration
- decision:waypoint:2026-03-29:routine-pack-authoring-surfaces
- session-note:waypoint:2026-03-29:routine-pack-architecture-exploration

## Verification

- The definition covers the human authoring lifecycle for create, inspect, edit, validate, preview, diff, and publish flows for routines and routine packs.
- The role split between Telegram, Web UI, and MCP is explicit and does not leave Telegram as the assumed primary editing environment.
- The proposed API and domain boundary are provider-neutral and do not encode transport-specific UI logic into Telegram or provider adapters.
- The definition identifies which authoring artifacts are ephemeral runtime or draft state and which durable outputs must flow into project-memory.

## Evidence

- none
