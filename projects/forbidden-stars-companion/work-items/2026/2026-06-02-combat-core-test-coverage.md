---
date: 2026-06-02
recorded_at: 2026-06-02T14:08:47.519Z
project: forbidden-stars-companion
topic: combat-core-test-coverage
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Начать разумное покрытие проекта юнит-тестами с rule-driven ядра, не блокируя разработку до полного покрытия всего приложения.

## Outcome

Тестами покрыты src/combat/calculations.ts, src/combat/actions.ts, src/combat/analysis/requisiteCheck.ts и стабильные части src/combat/effects/executor.ts; добавлен базовый test harness для дальнейшего расширения.

## Provenance

- ad-hoc: Выделено по итогам аудита репозитория, project-memory и официальных rule sources 2026-06-02

## Dependencies

- none

## Context

- canonical-doc:forbidden-stars-companion:development-workflow:development-workflow
- canonical-doc:forbidden-stars-companion:combat-engine:combat-engine
- canonical-doc:forbidden-stars-companion:combat-effects:combat-effects
- session-note:forbidden-stars-companion:2026-06-02:initial-project-memory-fill

## Verification

- Добавить и запустить test runner в проекте.
- Убедиться, что unit tests проходят локально.
- Проверить тестами dice count, morale totals, rout/rally, requisites и поддержанные effect primitives.
- Подтвердить, что тесты не фиксируют заведомо неверное текущее поведение как канон.

## Evidence

- none
