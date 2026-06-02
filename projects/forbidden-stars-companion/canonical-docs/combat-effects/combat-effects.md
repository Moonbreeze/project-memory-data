---
date: 2026-06-02
recorded_at: 2026-06-02T11:42:59.251Z
project: forbidden-stars-companion
topic: combat-effects
registry_scope: combat-effects
source: agent
status: active
---
# Canonical Doc

## Summary

Эффекты боевых карт формализованы как typed effect DSL с автоматическим исполнением и отдельной моделью pending input для эффектов, требующих выбора пользователя.

## Guidance

- `src/combat/effects/types.ts` определяет DSL боевых эффектов: gain/lose tokens, gain/lose/convert/reroll dice, route/rally/destroy units, conditional branches, per-unit и per-die эффекты, а также специальные card mechanics.
- Эффекты, которые можно применить детерминированно, должны исполняться автоматически через executor без участия UI.
- Эффекты, требующие выбора игрока или ветвления, должны возвращать `PendingInput`, который UI может безопасно отобразить и дозавершить.
- Пассивные или плохо моделируемые внутри текущего приложения эффекты допустимо хранить как формализованные маркеры или `boardEffect`, не притворяясь, что приложение уже полностью их исполняет.
- Формализация эффектов служит не только для live resolution, но и для статического анализа карт и вариантов хода.
- Если правила или FAQ задают поведение, которое приложение пока не может корректно исполнить автоматически, канонический документ должен считать первичным правило, а не текущую техническую границу кода.

## References

- pdf:/home/moonbreeze/Forbidden Stars - Rules Reference.pdf
- pdf:/home/moonbreeze/forbidden_stars_faq_1.1.pdf
- file:/home/moonbreeze/forbidden-stars-companion/src/combat/effects/types.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/combat/effects/executor.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/combatCardEffectsData.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/stores/combatStore.ts
