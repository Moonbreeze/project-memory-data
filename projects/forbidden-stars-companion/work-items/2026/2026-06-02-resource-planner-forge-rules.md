---
date: 2026-06-02
recorded_at: 2026-06-02T14:08:16.860Z
project: forbidden-stars-companion
topic: resource-planner-forge-rules
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Исправить planner покупок под реальные правила forge/cache/command level.

## Outcome

Planner корректно считает снижение command requirement на 1, оплату forge-cost, запрет применения forge к upgrades и комбинации из FAQ.

## Provenance

- ad-hoc: Выделено по итогам аудита репозитория, project-memory и официальных rule sources 2026-06-02

## Dependencies

- none

## Context

- canonical-doc:forbidden-stars-companion:resource-planning:resource-planning
- canonical-doc:forbidden-stars-companion:rules-sources:rules-sources
- canonical-doc:forbidden-stars-companion:core-use-cases:core-use-cases
- session-note:forbidden-stars-companion:2026-06-02:initial-project-memory-fill

## Verification

- Проверить покупку unit с forge cost при достаточном числе forge tokens.
- Проверить снижение command requirement unit на 1 через forge token.
- Проверить, что forge не применяется к upgrades.
- Проверить несколько mixed purchase scenarios с cache и forge одновременно.

## Evidence

- none
