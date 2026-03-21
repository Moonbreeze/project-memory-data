---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: decompose-oversized-core-and-mcp-modules
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Track the architectural follow-up from code review to decompose oversized core and MCP modules into smaller units with clearer responsibilities.

## Outcome

The repository has a tracked implementation slice for decomposing oversized modules such as boundedReads and MCP input parsing into narrower files, and for addressing the current server state shape where that refactor materially improves testability without changing behavior.

## Provenance

- ad-hoc: Planned from the 2026-03-21 code review findings covering oversized modules, parser concentration, and testability concerns in the server state layer.

## Dependencies

- none

## Context

- none

## Verification

- Verify src/core/boundedReads is decomposed into smaller files with preserved bounded-read behavior and stage semantics.
- Verify src/mcp/types parsing responsibilities are split into clearer modules without changing JSON-RPC or tool input behavior.
- Verify MCP server state handling is either encapsulated into a more testable structure or explicitly left unchanged with documented rationale after the refactor.
- Verify the existing automated test suite still passes after the decomposition work.

## Evidence

- session-note:project-memory:2026-03-21:decompose-oversized-core-and-mcp-modules
- verification-result:project-memory:2026-03-21:decompose-oversized-core-and-mcp-modules
