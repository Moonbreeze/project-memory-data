---
date: 2026-06-02
recorded_at: 2026-06-02T11:41:09.759Z
project: forbidden-stars-companion
topic: core-use-cases
registry_scope: core-use-cases
source: agent
status: active
---
# Canonical Doc

## Summary

Основные сценарии использования приложения связаны с живой партией: помощь в бою, отслеживание боевых колод, планирование ресурсоёмких покупок и использование таймеров.

## Guidance

- Во время боя приложение должно помогать быстро собрать состояние столкновения, применить эффекты карт, оценить возможные варианты хода и увидеть последствия по offence, defence и morale.
- Приложение должно поддерживать отслеживание текущего состава боевой колоды игрока, включая замену базовых карт апгрейдами.
- Страница ресурсов должна помогать планировать покупки на ход с учётом materiel, cache, forge, command level и состава доступных юнитов и апгрейдов.
- Таймерная подсистема должна помогать регулировать темп партии в стратегическом и боевом режимах без необходимости дополнительного оборудования.
- Все ключевые use case'ы предполагают использование рядом с физической партией, а не автономное моделирование всей игры без настольного компонента.

## References

- chat:user-direction:2026-06-02:core-use-cases
- file:/home/moonbreeze/forbidden-stars-companion/src/pages/CombatPage.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/pages/ResourcesPage.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/pages/TimerPage.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/stores/sessionStore.ts
