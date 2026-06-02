---
date: 2026-06-02
recorded_at: 2026-06-02T14:08:16.934Z
project: forbidden-stars-companion
topic: analysis-alignment-with-real-combat
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Синхронизировать анализатор карт с реальным боевым состоянием и полной runtime-реализацией эффектов карт.

## Outcome

Hints строятся только по реально доступным картам и опираются на те же правила и effect semantics, что и runtime; analysis и runtime не расходятся по поддерживаемым card effects.

## Provenance

- ad-hoc: Выделено по итогам аудита репозитория, project-memory и официальных rule sources 2026-06-02

## Dependencies

- work-item:forbidden-stars-companion:2026-06-02:complete-card-effect-resolution
- work-item:forbidden-stars-companion:2026-06-02:real-deck-and-hand-model-in-combat

## Context

- canonical-doc:forbidden-stars-companion:combat-analysis:combat-analysis
- canonical-doc:forbidden-stars-companion:combat-effects:combat-effects
- canonical-doc:forbidden-stars-companion:combat-cards-and-decks:combat-cards-and-decks
- session-note:forbidden-stars-companion:2026-06-02:initial-project-memory-fill

## Verification

- Сравнить несколько card analyses с реальным разыгрыванием тех же карт в одинаковом combat state.
- Проверить, что analysis использует фактическую доступность карт из hand/deck model.
- Проверить, что после добавления новых card effects analysis и runtime обновляются согласованно.
- Подтвердить на representative наборе карт всех фракций, что analysis не расходится с фактическим runtime outcome по поддерживаемым сценариям.

## Evidence

- none
