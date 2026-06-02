---
date: 2026-06-02
recorded_at: 2026-06-02T14:08:16.821Z
project: forbidden-stars-companion
topic: complete-card-effect-resolution
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Довести исполнение формализованных эффектов карт до полного рабочего состояния.

## Outcome

enemyChoice/selfChoice, pending inputs, passive effects и special effects исполняются корректно в runtime в рамках целевой модели приложения; скрытых no-op для card effects не остаётся.

## Provenance

- ad-hoc: Выделено по итогам аудита репозитория, project-memory и официальных rule sources 2026-06-02

## Dependencies

- none

## Context

- canonical-doc:forbidden-stars-companion:combat-effects:combat-effects
- canonical-doc:forbidden-stars-companion:combat-engine:combat-engine
- canonical-doc:forbidden-stars-companion:rules-sources:rules-sources
- session-note:forbidden-stars-companion:2026-06-02:initial-project-memory-fill

## Verification

- Проверить карты с branch choice, где результат реально влияет на combat state.
- Проверить карты с pending input по unit, dice и token choice.
- Сверить representative card effects всех фракций с Rules Reference, FAQ и текстом карт.
- Подтвердить, что card effects больше не требуют неявного manual resolution там, где они входят в scope runtime.

## Evidence

- none
