---
date: 2026-03-24
recorded_at: 2026-03-24T00:00:00.000Z
project: waypoint
topic: claude-approval-smoke-validation
source: user
status: active
work_item_state: open
---
# Work Item

## Summary

Добиться conclusive результата Claude approval smoke — подобрать prompt или конфигурацию, при которой Claude реально эмитит approval request вместо auto-approve.

## Outcome

Live smoke с LIVE_SMOKE_CLAUDE_APPROVAL=1 проходит conclusively: approval request реально эмитится, проходит через approval router, решение доставляется обратно провайдеру, turn завершается.

## Provenance

- ad-hoc: Claude approval smoke оставался inconclusive с 2026-03-11 — бэкенд auto-approve'ит операции вместо эмиссии approval request. Нужен prompt, вызывающий реальный approval.

## Dependencies

- none

## Context

- none

## Verification

- LIVE_SMOKE_CLAUDE_APPROVAL=1 проходит с реальным approval request (не auto-approve)
- Verification-result зафиксирован с конкретным prompt и результатом

## Evidence

- none
