---
date: 2026-04-12
recorded_at: 2026-04-12T16:58:44.279Z
project: project-memory
topic: runbook-upsert-surface
source: agent
status: active
---
# Session Note

## Summary

Implemented a canonical runbook upsert surface across core, MCP, and CLI while keeping legacy create aliases working.

## Actions

- Renamed the core mutable runbook write helper to `upsertRunbook` and kept `createRunbook` as a legacy alias.
- Added primary `upsert_runbook` and `upsert-runbook` write surfaces and updated chooser guidance to recommend the new MCP tool.
- Updated lifecycle-facing docs to state that stable-guidance surfaces replace current documents in place and added alias coverage in CLI and MCP tests.
- Ran `node --experimental-strip-types --test tests/core/documentFlow.test.ts tests/mcp/server.test.ts tests/cli/cliFlow.test.ts` and confirmed the targeted suites passed.

## Follow-up

- Consider a later cleanup pass to mark legacy create aliases deprecated in any remaining user-facing command reference surfaces if broader CLI/MCP help text expands.
