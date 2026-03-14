---
date: 2026-03-12
project: claude-remote
topic: remaining-migration-sessions
source: agent
status: active
---
# Runbook

## Purpose

Track the remaining execution backlog after the large multi-provider refactor, based on docs/nextSessions.md.

## Procedure

- Treat docs/nextSessions.md as the session-scoped execution backlog and run only one listed session per work session unless scope is explicitly broadened.
- Assume Session 1 (plan reconciliation), Session 2 (structured user input honesty), and Session 3 (Web verification hardening) are already completed as of 2026-03-11.
- Treat Session 4 (Live Verification) as partially complete: automated build, test, and opt-in live smoke coverage are recorded, but real approval flows, Telegram end-to-end checks, Web live checks, and Claude elicitation edge cases still remain open.
- Treat Session 5 (Final Cleanup And Closure) as the current remaining cleanup pass: align docs with the final implementation, remove or mark unsupported or experimental leftovers, review package.json for stale migration remnants, and confirm KNOWN_BUGS.md contains only active items.
- When executing any session, read docs/nextSessions.md plus the relevant part of MULTI_PROVIDER_REFACTOR_PLAN.md first, keep scope local, preserve provider-neutral boundaries, and update docs in the same session when behavior changes.
- If a real bug is discovered during a session, add or update a regression test and record it in src/__tests__/KNOWN_BUGS.md.

## Verification

- After meaningful changes, run npm run build.
- Run the narrowest relevant vitest subset before broader test coverage.
- Treat Web server failures caused only by local listen(...) restrictions as environment limitations, not product regressions, unless application evidence says otherwise.
- Final session reporting should explicitly state what changed, what was verified, any unresolved risks, and whether the session acceptance criteria were fully met.
