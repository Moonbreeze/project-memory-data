---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: remaining-migration-sessions
source: agent
status: archived
---
# Runbook

## Purpose

Summarize the remaining migration and closure arc now that executable backlog lives in project-memory work items instead of the repo-local nextSessions document.

## Procedure

- Use the project planning backlog, not a repo-local markdown file, as the executable source for the remaining migration work.
- Treat the large runtime migration as functionally complete: the provider-neutral core, persistence, Telegram transport, Web transport, Claude provider, Codex provider, and composition root are already present, and the legacy tmux runtime path has already been removed from `src/`.
- Treat the main remaining gaps as: missing recorded Codex feasibility artifacts, incomplete manual live verification closure, and final cleanup so the repository reflects a post-migration maintenance state instead of an in-progress refactor state.
- Preserve the working rules from the old session backlog: keep scope local, prefer additive or local changes over broad rewrites, keep provider boundaries provider-neutral, update docs when behavior changes, and record any real bug in `src/__tests__/KNOWN_BUGS.md` with regression coverage.
- Preserve the verification rules from the old session backlog: run `npm run build` after meaningful changes, start with the narrowest relevant vitest subset, broaden after the narrow checks pass, and treat Web test failures caused only by denied local `listen(...)` as environment limitations unless stronger product evidence exists.
- Use the managed work items `codex-feasibility-artifacts`, `manual-live-verification-closure`, and `migration-final-cleanup-closure` as the explicit remaining backlog slices rather than reviving session-numbered repo docs.
- When reporting a session, state what changed, what was verified, any unresolved risks, and whether the work-item acceptance criteria were fully met.

## Verification

- Historical state from 2026-03-11: the old Session 1 plan reconciliation, Session 2 structured user-input honesty work, and Session 3 Web verification hardening were completed.
- Historical state from 2026-03-11: the old Session 4 live verification was only partially completed because approval flows remained inconclusive under local auto-approval policy and interactive Telegram and Web checks were not fully exercised.
- The project planning backlog was intentionally empty before this migration; managed work items now carry the remaining executable backlog explicitly.
