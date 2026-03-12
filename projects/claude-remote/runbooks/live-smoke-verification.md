---
date: 2026-03-12
project: claude-remote
topic: live-smoke-verification
source: agent
status: active
project_commit: a9f3e30b3e57de375a441f44623a26e4cac3a3e6
---
# Runbook

## Purpose

Capture the opt-in real-backend smoke workflow from docs/liveSmokeTests.md for the migrated runtime path.

## Procedure

- Run npm run test:live explicitly; the suite is intentionally outside the default npm test path.
- Enable provider scenarios only with the relevant flags: LIVE_SMOKE_CLAUDE=1, LIVE_SMOKE_CODEX=1, LIVE_SMOKE_CLAUDE_APPROVAL=1, LIVE_SMOKE_CODEX_APPROVAL=1, LIVE_SMOKE_CLAUDE_RESUME=1, LIVE_SMOKE_CODEX_RESUME=1.
- Provide any required prompt overrides, especially LIVE_SMOKE_CLAUDE_APPROVAL_PROMPT and LIVE_SMOKE_CODEX_APPROVAL_PROMPT when approval smoke is enabled.
- Use LIVE_SMOKE_WORK_DIR, LIVE_SMOKE_TIMEOUT_MS, CLAUDE_MODEL, and CODEX_MODEL as needed; Codex smoke depends on a working codex CLI on PATH and uses codex app-server over stdio only.
- Interpret pass as: a new provider-backed session was created through the migrated runtime, the turn completed, and the rendered output contained the expected smoke token.
- Interpret failure as: provider error, timeout, only an approval request without completion, or output missing the expected token. Treat approval runs that are auto-approved without an explicit approval request as inconclusive rather than passed.

## Verification

- Recorded state on 2026-03-11: npm run build passed, npm test passed, npm run test:live without flags skipped safely, Claude live smoke passed, Codex live smoke passed outside the restricted sandbox, and Claude/Codex resume smoke passed outside the restricted sandbox.
- Approval smoke for both providers remained inconclusive in the recorded environment because the candidate operations were auto-approved instead of surfacing explicit approval requests.
- If Codex live smoke fails only inside the restricted sandbox but passes outside it, record that as an environment restriction rather than a runtime regression.
- Use the broader manual verification checklist after live smoke when Telegram, Web, approval UX, or real process lifecycle behavior still need confirmation.
