---
date: 2026-06-02
recorded_at: 2026-06-02T14:08:47.506Z
project: forbidden-stars-companion
topic: pending-input-ui-fixes
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Довести overlay выбора эффектов до корректного UX и данных.

## Outcome

Выбор юнитов использует unit data, branch options показывают реальные варианты, manual fallback отделён от fully supported flow.

## Provenance

- ad-hoc: Выделено по итогам аудита репозитория, project-memory и официальных rule sources 2026-06-02

## Dependencies

- none

## Context

- canonical-doc:forbidden-stars-companion:combat-effects:combat-effects
- canonical-doc:forbidden-stars-companion:ui-shell:ui-shell
- session-note:forbidden-stars-companion:2026-06-02:initial-project-memory-fill

## Verification

- Проверить chooseUnit overlay для route, rally и destroy.
- Проверить chooseDice overlay для reroll и convert.
- Проверить chooseTokenType и chooseBranch overlays.
- Проверить, что UI не подставляет card data вместо unit data.

## Evidence

- none
