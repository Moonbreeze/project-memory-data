---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: enum-validation-surface-for-mcp
source: agent
status: active
---
# Session Note

## Summary

Implemented a shared enum-surface and enum-validation UX improvement for MCP and aligned the taxonomy-registry CLI path with the same actionable allowed-value guidance.

## Actions

- Added a shared MCP schema helper for enum-constrained string properties and switched tool definitions to core enum arrays instead of local literals.
- Added a shared MCP parser helper that reports invalid enum-like values with explicit allowed values across taxonomy, document metadata, work-item, lifecycle, and list query parameters.
- Aligned `upsert-taxonomy-registry` CLI entry parsing so invalid taxonomy registry state or migration values return actionable allowed-value guidance.
- Added regression tests for `tools/list` nested taxonomy enum exposure and invalid migration error text in MCP and CLI, then ran targeted and full test suites.

## Follow-up

- Apply the same UX standard to non-enum structured validation paths if future agent friction shows the same recovery problem outside enum-like fields.
