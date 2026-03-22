---
date: 2026-03-22
recorded_at: 2026-03-22T10:56:56.481Z
project: waypoint
topic: codex-live-smoke-approval-fix
source: agent
status: active
---
# Verification Result

## Scope

Codex live smoke outside sandbox after liveRuntimeHarness approval-state fix

## Steps

- Ran `npx vitest run src/__tests__/liveRuntimeHarness.test.ts` to verify the harness stops auto-clicking once Telegram clears the approval keyboard.
- Ran `npx vitest run src/__tests__/codexProvider.test.ts` to verify approval override wiring remained correct.
- Ran `npm run build` to verify the TypeScript build after the harness and Codex provider changes.
- Ran `env LIVE_SMOKE_CODEX=1 LIVE_SMOKE_CODEX_RESUME=1 LIVE_SMOKE_CODEX_APPROVAL=1 LIVE_SMOKE_CODEX_APPROVAL_POLICY=untrusted LIVE_SMOKE_CODEX_APPROVAL_PROMPT='Run the shell command touch /tmp/waypoint-codex-approval-smoke.txt && echo LIVE_SMOKE_CODEX_APPROVAL_OK, then reply with the exact token LIVE_SMOKE_CODEX_APPROVAL_OK and nothing else.' LIVE_SMOKE_TIMEOUT_MS=120000 npm run test:live` outside the sandbox.
- Observed `src/liveSmoke/liveSmoke.test.ts` pass for Codex basic, approval, and resume; no `Exceeded maxAutoApprovals` failure remained.

## Result

Passed. Targeted tests (`src/__tests__/liveRuntimeHarness.test.ts`, `src/__tests__/codexProvider.test.ts`) passed, `npm run build` passed, and `npm run test:live` with Codex live vars outside sandbox passed for basic, approval, and resume scenarios while Claude scenarios remained intentionally skipped.
