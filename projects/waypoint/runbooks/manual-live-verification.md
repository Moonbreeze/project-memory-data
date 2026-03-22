---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: manual-live-verification
source: agent
status: active
---
# Runbook

## Purpose

Preserve the full live verification checklist for the migrated runtime after automated tests and live smoke pass, replacing the repo-local manualVerification document.

## Procedure

- Before starting, run `npm run build` and `npm test`, prepare a real `.env`, and confirm access to `BOT_TOKEN`, `ALLOWED_USERS`, `DEFAULT_PROVIDER`, `DEFAULT_WORK_DIR`, `PERSISTENCE_PATH`, `CLAUDE_MODEL`, `CODEX_MODEL`, `WEB_PORT`, and `WEB_TOKEN` as needed.
- Use a dedicated persistence path for manual verification rather than production state.
- Use the minimum live matrix: Telegram plus Claude, Telegram plus Codex, restart or restore or resume on persisted state, and approval flow on each provider.
- Verify Telegram runtime behavior through `/start`, `/new`, normal text messages, `/sessions`, `/switch`, `/status`, and `/kill`, and confirm that the bot process routes everything through the migrated runtime path.
- Verify quick temporary session behavior through `/q` and `/quick` and confirm that the normal current-session pointer is restored afterward and temporary sessions do not remain in persisted state.
- For Claude, verify approval behavior against the real backend and also exercise user-input or elicitation edge cases that the current Telegram UI cannot fully satisfy; unsupported flows must stay user-visible and must not fail silently.
- For Codex, verify command streaming, plan updates, approval requests, event ordering, approval button mapping, and final session status against the real `codex app-server` backend over `stdio`.
- Verify restart, restore, and resume by creating a real session, stopping the app gracefully, restarting with the same persistence path, and confirming that the restored session resumes the provider conversation instead of starting an unrelated thread.
- If the Web transport is enabled, verify bearer auth, `POST /sessions`, `POST /sessions/:id/messages`, `POST /approvals/:id`, and `WS /events` against a live process.
- When a backend auto-approves the candidate action instead of emitting an approval request, record the run as inconclusive for approval rather than passing it. Whenever live behavior differs from expectations, record the exact backend behavior and confirm that the session remains recoverable.

## Verification

- The regular automated suite already covers scripted provider-neutral runtime flows, quick-session handling, restart on scripted providers, provider tests, and Web server contract tests.
- Manual live verification is still required for real Claude and Codex backend behavior, real Telegram delivery and callbacks, real Web HTTP and WebSocket behavior, provider-specific approval or user-input edge cases, and real lifecycle behavior around startup, shutdown, and resume.
- Phase-10-style manual verification can be considered substantially complete only when Telegram plus Claude, Telegram plus Codex, approval flow on both providers, restart or resume on real persisted sessions, known Claude elicitation limitations, and the live Web path if intended for deployment are all either verified or explicitly documented as skipped with reason.
