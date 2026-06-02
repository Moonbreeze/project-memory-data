---
date: 2026-06-02
recorded_at: 2026-06-02T14:08:16.907Z
project: forbidden-stars-companion
topic: combat-setup-validation
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Добавить rule-aware валидацию setup боя.

## Outcome

Setup блокирует или явно маркирует невалидные стартовые состояния, включая лимит attacking units и особые стартовые условия.

## Provenance

- ad-hoc: Выделено по итогам аудита репозитория, project-memory и официальных rule sources 2026-06-02

## Dependencies

- none

## Context

- canonical-doc:forbidden-stars-companion:combat-engine:combat-engine
- canonical-doc:forbidden-stars-companion:ui-shell:ui-shell
- canonical-doc:forbidden-stars-companion:core-use-cases:core-use-cases
- session-note:forbidden-stars-companion:2026-06-02:initial-project-memory-fill

## Verification

- Попытаться создать setup с превышением допустимых attacking units и проверить реакцию UI.
- Попытаться создать setup без валидной defending side и проверить обработку.
- Проверить, что valid setup scenarios продолжают проходить без лишних блокировок.

## Evidence

- none
