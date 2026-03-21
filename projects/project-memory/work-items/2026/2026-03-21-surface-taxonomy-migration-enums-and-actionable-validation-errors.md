---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: surface-taxonomy-migration-enums-and-actionable-validation-errors
source: user
status: active
work_item_state: done
---
# Work Item

## Summary

Fix MCP/agent UX so taxonomy registry migration markers are discoverable from the tool contract or from actionable validation errors without requiring source inspection.

## Outcome

Agents can use taxonomy registry write surfaces without reading implementation code to discover valid migration markers because enum-constrained values are surfaced through the agent-visible tool contract, actionable validation errors, or both.

## Provenance

- ad-hoc: Planned from user-reported UX defect: the agent-facing MCP tool surface did not expose allowed taxonomy migration enum values, and runtime validation returned a generic error instead of actionable allowed-value guidance.

## Dependencies

- none

## Context

- none

## Verification

- Verify the agent-visible tool surface for `upsert_taxonomy_registry` exposes the allowed `migration` values or an equivalent machine-readable constraint.
- Verify invalid `migration` input returns an actionable validation error that includes the allowed values or a direct pointer to them.
- Verify the same UX expectation is applied consistently to similar enum-constrained MCP write parameters rather than fixing only this one field.
- Verify the documented behavior makes source inspection unnecessary for routine recovery from invalid enum-like input.

## Evidence

- verification-result:project-memory:2026-03-21:enum-validation-and-tool-schema-surface
- session-note:project-memory:2026-03-21:enum-validation-surface-for-mcp
