---
date: 2026-04-12
recorded_at: 2026-04-12T16:58:35.410Z
project: project-memory
topic: runbook-upsert-surface
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Add a canonical upsert surface for runbook updates while preserving backward compatibility for existing create aliases.

## Outcome

Runbook guidance updates use an explicit upsert contract across core, MCP, and CLI, with backward-compatible create aliases retained and validated.

## Provenance

- ad-hoc: Codify runbook updates as an explicit mutable stable-guidance surface instead of relying on create semantics that already replace in place.

## Dependencies

- none

## Context

- none

## Verification

- Add explicit `upsert_runbook` and `upsert-runbook` surfaces while keeping `create_runbook` and `create-runbook` as backward-compatible aliases.
- Update chooser and lifecycle-facing docs so runbook updates use the same mutable contract language as other stable-guidance surfaces.
- Run targeted automated tests covering core, MCP, and CLI behavior for the new primary surface and legacy aliases.

## Evidence

- session-note:project-memory:2026-04-12:runbook-upsert-surface
- verification-result:project-memory:2026-04-12:runbook-upsert-surface
