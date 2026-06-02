---
date: 2026-06-02
recorded_at: 2026-06-02T11:42:59.305Z
project: forbidden-stars-companion
topic: resource-planning
registry_scope: resource-planning
source: agent
status: active
---
# Canonical Doc

## Summary

Подсистема ресурсов предназначена для планирования покупок на ход с учётом materiel, cache, forge, command level и доступных апгрейдов, а не для полного трекинга всех фаз партии.

## Guidance

- Страница ресурсов должна помогать игрокам оценивать, что они могут купить в текущем или следующем ходу при ограниченном бюджете materiel.
- При планировании нужно учитывать official constraints: command level по числу cities, cache только для unit/structure, forge для unit requirements и лимиты asset tokens.
- Подсистема должна оставаться planner'ом, а не полной бухгалтерией всех order resolutions и board-state изменений.
- Текущее сессионное состояние может хранить территории, objective tokens и купленные улучшения настолько, насколько это помогает ресурсному planning use case.
- При расхождении между planner-логикой и rule sources приоритет имеют Rules Reference и FAQ.

## References

- pdf:/home/moonbreeze/Forbidden Stars - Rules Reference.pdf
- pdf:/home/moonbreeze/forbidden_stars_faq_1.1.pdf
- file:/home/moonbreeze/forbidden-stars-companion/src/pages/ResourcesPage.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/stores/sessionStore.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/units.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/upgrades.ts
