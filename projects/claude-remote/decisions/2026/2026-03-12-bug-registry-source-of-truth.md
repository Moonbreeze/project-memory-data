---
date: 2026-03-12
project: claude-remote
topic: bug-registry-source-of-truth
source: agent
status: archived
---
# Decision

## Context

The repository keeps an explicit known-bugs registry in src/__tests__/KNOWN_BUGS.md. Future sessions may benefit from remembering that active bug state through project-memory, but duplicating the entire registry in two mutable places would create drift risk.

## Decision

Keep src/__tests__/KNOWN_BUGS.md as the canonical bug registry and regression index. Use project-memory only for lightweight summaries of active bug state when that context helps future sessions start faster, not as a second authoritative bug database.

## Consequences

- When a new bug is discovered, it must still be added to src/__tests__/KNOWN_BUGS.md and covered by a regression test there.
- Project-memory may record the currently active bug snapshot or major bug-state changes, but it should not replace or diverge from the repository file.
- Future cleanup sessions should verify that project-memory bug summaries still match the active repo registry before relying on them.
