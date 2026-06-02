---
date: 2026-06-02
recorded_at: 2026-06-02T11:42:59.352Z
project: forbidden-stars-companion
topic: reference-content
registry_scope: reference-content
source: agent
status: active
---
# Canonical Doc

## Summary

Справочная страница приложения — это быстрый in-app reference по фракциям, юнитам, боевым картам, апгрейдам приказов и фазам игры на основе внутренних data tables и официальных PDF-источников.

## Guidance

- Справочник предназначен для быстрого обращения во время партии и должен быть производным от статического data layer, а не отдельным независимым источником знаний.
- Справочная страница может показывать упрощённые правила и описания, но её содержимое должно оставаться согласованным с Rules Reference, FAQ и Database.
- Если правила игры в PDF отличаются от текста в приложении, приоритет у внешних rule sources; расхождение должно рассматриваться как задача синхронизации данных или UI-текста.
- Справочник не обязан дублировать полный rules reference; его задача — быстрое table-side напоминание по наиболее нужным данным и фазам.

## References

- file:/home/moonbreeze/forbidden-stars-companion/src/pages/ReferencePage.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/data/units.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/combatCards.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/upgrades.ts
- pdf:/home/moonbreeze/Forbidden Stars - Rules Reference.pdf
- pdf:/home/moonbreeze/Forbidden_Stars_Database.pdf
