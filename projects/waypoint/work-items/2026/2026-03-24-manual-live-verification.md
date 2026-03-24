---
date: 2026-03-24
recorded_at: 2026-03-24T00:00:00.000Z
project: waypoint
topic: manual-live-verification
source: user
status: active
work_item_state: blocked
---
# Work Item

## Summary

Провести полную ручную верификацию runtime с реальными бэкендами Claude и Codex через Telegram, включая approval UX, restart/resume, и опционально Web transport.

## Outcome

Все сценарии из runbook manual-live-verification пройдены или явно задокументированы как пропущенные с причиной. Результаты зафиксированы в verification-result.

## Provenance

- ad-hoc: Остаток фазы 10 из MULTI_PROVIDER_REFACTOR_PLAN.md — единственный незакрытый блок верификации после завершения всех фаз реализации.

## Dependencies

- none

## Context

- none

## Verification

- Telegram + Claude: /new, текстовый запрос, tool approval, /sessions, restart, resume frozen session
- Telegram + Codex: создание сессии, command streaming, approval, завершение turn, resume thread
- /q temporary session для обоих провайдеров
- Graceful shutdown и закрытие открытых handles
- Web transport (опционально): bearer auth, POST /sessions, POST /sessions/:id/messages, POST /approvals/:id, WS /events

## Evidence

- none
