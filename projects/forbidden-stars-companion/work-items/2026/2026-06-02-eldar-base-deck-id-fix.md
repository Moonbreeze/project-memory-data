---
date: 2026-06-02
recorded_at: 2026-06-02T14:08:47.485Z
project: forbidden-stars-companion
topic: eldar-base-deck-id-fix
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Исправить неконсистентный card ID в стартовой Eldar deck.

## Outcome

Стартовая Eldar combat deck использует те же ID, что и data layer, без битых ссылок.

## Provenance

- ad-hoc: Выделено по итогам аудита репозитория, project-memory и официальных rule sources 2026-06-02

## Dependencies

- none

## Context

- canonical-doc:forbidden-stars-companion:combat-cards-and-decks:combat-cards-and-decks
- canonical-doc:forbidden-stars-companion:game-data:game-data
- session-note:forbidden-stars-companion:2026-06-02:initial-project-memory-fill

## Verification

- Стартовать сессию за Eldar и проверить, что все стартовые cards находятся через combatCardsById.
- Проверить, что Eldar deck корректно участвует в draw/play flow.
- Проверить, что upgrade replacement для Eldar не ломает deck state.

## Evidence

- session-note:forbidden-stars-companion:2026-06-02:eldar-base-deck-id-fix
- verification-result:forbidden-stars-companion:2026-06-02:eldar-base-deck-id-fix
