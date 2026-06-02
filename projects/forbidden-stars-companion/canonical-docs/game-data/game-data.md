---
date: 2026-06-02
recorded_at: 2026-06-02T11:41:48.497Z
project: forbidden-stars-companion
topic: game-data
registry_scope: game-data
source: agent
status: active
---
# Canonical Doc

## Summary

Игровые данные проекта организованы как статический справочный слой по четырём фракциям, их юнитам, бастионам, боевым картам и апгрейдам приказов.

## Guidance

- `src/data` хранит статические описания фракций, юнитов, бастионов, боевых карт и order upgrades в виде TypeScript-структур и lookup-таблиц.
- В текущем коде поддерживаются четыре фракции: Ultramarines, Orks, Eldar и Chaos.
- Боевые карты разделены на стартовые и upgrade-карты; `combatCardsById` собирает карточные данные и сливает с ними формализованные эффекты из `combatCardEffectsData`.
- Статический data layer должен оставаться независимым от UI и stores, чтобы его можно было использовать как для отображения справочника, так и для боевой логики и анализа.
- Для правил и значений приоритетен PDF Database и официальные rule sources; несоответствия между кодом и источниками нужно трактовать как проблему реализации, а не как новую норму.

## References

- file:/home/moonbreeze/forbidden-stars-companion/src/data/index.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/types.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/units.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/combatCards.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/combatCardEffectsData.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/upgrades.ts
- pdf:/home/moonbreeze/Forbidden_Stars_Database.pdf
