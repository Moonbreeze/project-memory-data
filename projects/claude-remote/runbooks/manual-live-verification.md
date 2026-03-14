---
date: 2026-03-12
project: claude-remote
topic: manual-live-verification
source: agent
status: active
---
# Runbook

## Purpose

Preserve the manual live verification checklist for the migrated runtime after automated tests and live smoke pass.

## Procedure

- Before starting, run npm run build and npm test, prepare a real .env, and confirm access to BOT_TOKEN, ALLOWED_USERS, DEFAULT_PROVIDER, DEFAULT_WORK_DIR, PERSISTENCE_PATH, CLAUDE_MODEL, CODEX_MODEL, WEB_PORT, and WEB_TOKEN as needed.
- Use a dedicated persistence path for verification runs rather than production state.
- Run the minimum live matrix: Telegram + Claude, Telegram + Codex, restart/restore/resume on persisted state, and approval flow on each provider.
- Verify Telegram runtime behavior through /start, /new, normal text messages, /sessions, /switch, /status, and /kill.
- Verify quick temporary session behavior through /q and /quick and confirm the normal current-session pointer is restored afterward.
- Verify Claude approval behavior, Claude user-input or elicitation edge cases, Codex command/plan/approval flow, restart/restore/resume continuity, and the Web transport path if enabled.
- When a backend auto-approves the candidate operation instead of emitting an approval request, record the run as inconclusive for approval rather than passing it.
- Record exact backend behavior whenever live provider behavior differs from expectations and keep sessions recoverable after limitations are hit.

## Verification

- The regular automated suite already covers scripted provider-neutral runtime flows, quick-session handling, restart flow on scripted providers, provider tests, and Web server contracts.
- Manual live verification is still required for real Claude and Codex backend behavior, real Telegram delivery and callbacks, real Web HTTP and WebSocket behavior, provider-specific approval or user-input edge cases, and real lifecycle behavior around startup, shutdown, and resume.
- If continuity after restart looks suspicious, inspect the persisted JSON rather than assuming provider failure.
