---
date: 2026-06-02
recorded_at: 2026-06-02T11:42:59.286Z
project: forbidden-stars-companion
topic: combat-analysis
registry_scope: combat-analysis
source: agent
status: active
---
# Canonical Doc

## Summary

Статический анализатор карт оценивает доступные боевые карты по наилучшему и наихудшему влиянию на offence, defence и morale, но не заменяет полный rules engine.

## Guidance

- Подсистема анализа предназначена для помощи игроку во время живой партии и должна объяснять потенциальную ценность доступных карт, а не симулировать весь game tree.
- Анализ строится поверх формализованных card effects и unit requisites, вычисляя min/max impact для offence, defence и morale со стороны владельца карты.
- Ветвящиеся и недетерминированные эффекты допускают диапазоны и notes вместо ложной точности.
- Анализ должен учитывать официальные ограничения правил, например requisites по unrouted units, persistence faceup cards и различие dice versus combat tokens.
- Канонически analysis — это слой decision support, а не источник истины по результату боя; источником истины по разрешению боя остаётся combat engine и официальные правила.

## References

- file:/home/moonbreeze/forbidden-stars-companion/src/combat/analysis/types.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/combat/analysis/analyzer.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/combat/analysis/requisiteCheck.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/pages/CombatPage.tsx
- pdf:/home/moonbreeze/Forbidden Stars - Rules Reference.pdf
