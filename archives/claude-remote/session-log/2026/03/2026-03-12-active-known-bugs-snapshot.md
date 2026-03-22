---
date: 2026-03-12
project: claude-remote
topic: active-known-bugs-snapshot
source: agent
status: active
---
# Session Note

## Summary

Recorded the current known-bug snapshot from src/__tests__/KNOWN_BUGS.md so future sessions can see the active regression state without reopening the file immediately.

## Actions

- Confirmed that src/__tests__/KNOWN_BUGS.md currently contains one active recorded bug.
- Captured Bug #1: concurrent jsonStore.save() operations in the migrated runtime could race on sessions.json.tmp and intermittently fail with ENOENT during rename.
- Noted that Bug #1 is covered by src/__tests__/jsonStore.test.ts.
- Recorded that tmux-specific bug entries were removed together with the deleted legacy runtime path in Phase 9.

## Follow-up

- If a new bug is found, update src/__tests__/KNOWN_BUGS.md first and then refresh the project-memory bug snapshot if the change is relevant for future sessions.
- If Bug #1 is resolved or re-scoped, update both the repository registry and this high-level memory snapshot so they stay aligned.
