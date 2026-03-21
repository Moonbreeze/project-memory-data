---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: fail-soft-backlog-reads-on-invalid-work-items
source: agent
status: active
---
# Verification Result

## Scope

Fail-soft backlog/list reads on invalid work-item documents

## Steps

- Run targeted node --experimental-strip-types --test tests/core/documentFlow.test.ts --test-name-pattern="readPlanningBacklog skips invalid done work-items".
- Run targeted node --experimental-strip-types --test tests/mcp/server.test.ts --test-name-pattern="invalid work-item diagnostics".
- Run full npm test.

## Result

All targeted regressions passed, and the full test suite passed after the fail-soft diagnostics changes.
