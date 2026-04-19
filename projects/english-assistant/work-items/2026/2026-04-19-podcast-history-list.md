---
date: 2026-04-19
recorded_at: 2026-04-19T16:31:25.533Z
project: english-assistant
topic: podcast-history-list
source: user
status: active
work_item_state: open
---
# Work Item

## Summary

Добавить список ранее созданных подкастов в интерфейсе и backend support для их получения.

## Outcome

Backend отдаёт коллекцию созданных подкастов, а UI показывает историю подкастов и позволяет открыть нужный элемент вместо работы только с одним текущим объектом в памяти клиента.

## Provenance

- ad-hoc: Requested by the user after confirming that the current product and UI expose only one currentPodcast without a browseable podcast list/history.

## Dependencies

- none

## Context

- none

## Verification

- Появляется backend endpoint для получения списка подкастов с ожидаемым порядком и полями, достаточными для UI.
- В интерфейсе пользователь видит несколько созданных подкастов и может выбрать любой из них для просмотра текущего статуса, script и audio state.
- Выбор существующего подкаста из списка корректно восстанавливает workflow state без regressions для create, confirm и synthesize flows.

## Evidence

- none
