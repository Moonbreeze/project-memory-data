---
date: 2026-06-02
recorded_at: 2026-06-02T11:41:48.343Z
project: forbidden-stars-companion
topic: app-architecture
registry_scope: app-architecture
source: agent
status: active
---
# Canonical Doc

## Summary

Приложение организовано как React/Vite SPA с отдельными страницами, Zustand stores и выделенным чистым доменным слоем `src/combat` для боевой логики.

## Guidance

- Точка входа приложения находится в `src/App.tsx`: до старта сессии отображается `SessionSetup`, после старта — маршрутизированное приложение с layout и четырьмя основными страницами.
- UI-страницы живут в `src/pages`, переиспользуемые оболочки — в `src/components`, пользовательское состояние — в `src/stores`, статические игровые данные — в `src/data`.
- Боевая логика намеренно вынесена из React/Zustand в `src/combat` как набор чистых типов, вычислений, действий, эффектов и аналитики.
- `combatStore` должен оставаться тонкой обёрткой вокруг чистого combat layer, а не вторым местом, где дублируется доменная логика боя.
- `sessionStore` и `timerStore` обслуживают прикладные сценарии приложения, но не должны размывать границы между UI-состоянием и правилами игры.
- При дальнейшем развитии архитектуры приоритетом остаётся ясное разделение: статические игровые данные, доменная логика, пользовательское состояние и рендеринг интерфейса.

## References

- file:/home/moonbreeze/forbidden-stars-companion/src/App.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/combat/index.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/stores/combatStore.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/stores/sessionStore.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/stores/timerStore.ts
