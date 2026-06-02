---
date: 2026-06-02
recorded_at: 2026-06-02T14:22:51.575Z
project: forbidden-stars-companion
topic: eldar-base-deck-id-fix
source: agent
status: active
---
# Session Note

## Summary

Исправлен неконсистентный Eldar starter combat card ID в session store и подтверждён корректный deck flow.

## Actions

- Найдено расхождение между Eldar starter deck в src/stores/sessionStore.ts и canonical combat card IDs в src/data/combatCards.ts.
- Исправлен стартовый ID с eld-command-of-the-autarch на eld-command-autarch в BASE_COMBAT_DECKS для фракции eldar.
- Подтверждено локальной сборкой npm run build, что проект после правки компилируется.
- Подтверждён runtime flow через временный esbuild bundle: startSession для Eldar создаёт валидную стартовую колоду, все card IDs находятся через combatCardsById, purchaseCombatUpgrade корректно заменяет две копии базовой карты на две копии upgrade-карты.

## Follow-up

- none
