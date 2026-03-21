---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: implement-project-scoped-managed-commit
source: agent
status: active
---
# Session Note

## Summary

Switched commit_pending_changes to a generated-subject contract with explicit project selection, updated managed decisions/work-item context, rebuilt ai-inst instructions, and verified the new project-scoped behavior end-to-end.

## Actions

- Created a new decision that replaces the redundant full-message contract with project plus summary input and archived the superseded selection decision.
- Updated the active work-item to target generated commit subjects and project-scoped selection semantics.
- Implemented the new commitPendingChanges contract across core, CLI, and MCP surfaces and rewrote tests for project-scoped multi-project behavior.
- Ran npm test successfully after the contract and test updates.
- Synced ai-inst rules and rebuilt AGENTS.md and CLAUDE.md for the repository.

## Follow-up

- Commit the managed project-memory documents for this completed slice.
- Commit the code-repository implementation changes if they should stay grouped as one changeset.
