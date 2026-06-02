---
date: 2026-06-02
recorded_at: 2026-06-02T14:08:16.842Z
project: forbidden-stars-companion
topic: real-deck-and-hand-model-in-combat
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Связать боевой экран с реальной боевой колодой игрока из session state.

## Outcome

В бою используются текущая deck composition, draw 5, played/discarded state и upgrade-modified deck вместо полного списка карт фракции.

## Provenance

- ad-hoc: Выделено по итогам аудита репозитория, project-memory и официальных rule sources 2026-06-02

## Dependencies

- none

## Context

- canonical-doc:forbidden-stars-companion:combat-cards-and-decks:combat-cards-and-decks
- canonical-doc:forbidden-stars-companion:session-model:session-model
- canonical-doc:forbidden-stars-companion:core-use-cases:core-use-cases
- session-note:forbidden-stars-companion:2026-06-02:initial-project-memory-fill

## Verification

- Купить combat upgrade и убедиться, что deck composition меняется корректно.
- Начать бой и проверить, что игрок видит только hand draw 5, а не все карты фракции.
- Проверить, что сыгранные карты корректно остаются faceup до конца боя.
- Проверить, что после боя карты возвращаются в deck state согласно модели приложения.

## Evidence

- none
