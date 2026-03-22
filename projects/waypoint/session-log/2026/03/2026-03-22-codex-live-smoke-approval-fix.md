---
date: 2026-03-22
recorded_at: 2026-03-22T10:56:56.485Z
project: waypoint
topic: codex-live-smoke-approval-fix
source: agent
status: active
---
# Session Note

## Summary

Fixed the live smoke approval loop by teaching the recording Telegram gateway to respect reply-markup edits, then verified the real Codex approval flow outside the sandbox.

## Actions

- Updated `src/liveSmoke/liveRuntimeHarness.ts` so approval detection and transcript button state are derived from the latest per-message reply markup, including `edit_reply_markup` events.
- Added `src/__tests__/liveRuntimeHarness.test.ts` to cover the regression where the harness re-clicked an already-cleared approval message.
- Extended the Codex live smoke path to pass explicit approval policy overrides and reran targeted tests plus the full Codex live smoke suite outside the sandbox.
- Confirmed the real Codex approval scenario now surfaces one approval request and completes successfully instead of failing with `Exceeded maxAutoApprovals=5`.

## Follow-up

- Decide whether to keep the new Codex approval-policy env knob documented in a runbook or provider note for future live-smoke operators.
- Clean up any temporary smoke artifacts such as the local untracked `approval-smoke.txt` file if it is no longer needed.
