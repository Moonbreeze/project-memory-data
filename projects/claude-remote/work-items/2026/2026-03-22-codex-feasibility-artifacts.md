---
date: 2026-03-22
recorded_at: 2026-03-22T09:30:48.258Z
project: claude-remote
topic: codex-feasibility-artifacts
source: agent
status: active
work_item_state: blocked
---
# Work Item

## Summary

Capture and record the missing manual feasibility artifacts for the real Codex app-server contract.

## Outcome

The missing feasibility-gate artifacts for `codex app-server` are recorded, and Codex support can be described as manually documented rather than only code-validated.

## Provenance

- ad-hoc: Remaining operational gap carried forward from the old docs/codexFeasibility and nextSessions documents.

## Dependencies

- none

## Context

- none

## Verification

- Run and capture `codex app-server --help`.
- Run and capture `codex app-server generate-json-schema --out <tmp-dir>`.
- Run and capture `codex app-server generate-ts --out <tmp-dir>`.
- Run and capture a minimal live handshake showing initialize, thread creation or resume, turn start, and representative notifications or requests.

## Evidence

- none
