---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: waypoint
topic: live-smoke-verification
source: agent
status: active
---
# Runbook

## Purpose

Capture the opt-in real-backend smoke workflow for the migrated runtime path as the managed operational reference, replacing the repo-local liveSmokeTests document.

## Procedure

- Run `npm run test:live` explicitly; the live smoke suite stays outside the default `npm test` path so regular automated runs remain offline and credential-independent.
- Enable provider scenarios only with the relevant flags: `LIVE_SMOKE_CLAUDE=1`, `LIVE_SMOKE_CODEX=1`, `LIVE_SMOKE_CLAUDE_APPROVAL=1`, `LIVE_SMOKE_CODEX_APPROVAL=1`, `LIVE_SMOKE_CLAUDE_RESUME=1`, and `LIVE_SMOKE_CODEX_RESUME=1`.
- Use `LIVE_SMOKE_WORK_DIR`, `LIVE_SMOKE_TIMEOUT_MS`, `CLAUDE_MODEL`, and `CODEX_MODEL` as needed; Claude smoke requires valid local Claude credentials, and Codex smoke requires a working `codex` CLI on `PATH` plus whatever auth the local Codex environment expects.
- When approval smoke is enabled, provide an explicit `LIVE_SMOKE_CLAUDE_APPROVAL_PROMPT` or `LIVE_SMOKE_CODEX_APPROVAL_PROMPT`; approval runs that do not actually surface an approval request are inconclusive, not passing.
- Treat the suite as covering the migrated runtime composition through `createAppRuntime(...)` with a recording Telegram gateway: new session creation, prompt submission, meaningful rendered outcome, and clean shutdown for the enabled provider scenarios.
- Do not treat the suite as a substitute for end-to-end Telegram or Web validation; it intentionally does not cover real Telegram delivery, real Web HTTP or WebSocket transport, broad conversation correctness, or the full manual approval and user-input checklist.
- Interpret pass as: the enabled provider scenario created a provider-backed session through the migrated runtime, completed the turn, and produced a rendered result containing the expected smoke token.
- Interpret failure as: provider error, timeout, only an approval request without completion, or output missing the expected smoke token. If Codex smoke fails only inside a restricted sandbox and passes outside it, record that as an environment restriction rather than a product regression.
- After live smoke passes, use the `manual-live-verification` runbook for the broader live Telegram, Web, approval UX, and restart scenarios that still require a real interactive process.

## Verification

- Recorded state on 2026-03-11: `npm run build` passed, `npm test` passed, `npm run test:live` without flags skipped safely, Claude live smoke passed, Codex live smoke passed outside the restricted sandbox, and Claude/Codex resume smoke passed outside the restricted sandbox.
- Recorded state on 2026-03-11: Claude and Codex approval smoke remained inconclusive because the candidate operations were auto-approved by the current provider policy instead of surfacing explicit approval requests.
- The Codex path is validated only for `codex app-server` over `stdio`; unsupported transports such as WebSocket remain out of scope until separately validated and implemented.
