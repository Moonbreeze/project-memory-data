---
date: 2026-06-02
recorded_at: 2026-06-02T11:41:48.514Z
project: forbidden-stars-companion
topic: development-workflow
registry_scope: development-workflow
source: agent
status: active
---
# Canonical Doc

## Summary

Проект разрабатывается как локальный frontend-репозиторий на React/Vite/TypeScript; основной operational workflow сейчас строится вокруг чтения rule sources, локальной сборки и проверки линта.

## Guidance

- Базовые команды проекта определены в `package.json`: `dev`, `build`, `lint`, `preview`.
- Содержательный анализ проекта нужно начинать не с шаблонного `README`, а с кода, `PLAN.md`, локальных инструкций и canonical project-memory документов.
- При изменении боевой логики сначала сверять правила по PDF rule sources, затем смотреть чистый combat layer и только потом stores/UI.
- Текущая кодовая база не содержит автоматических тестов; качество изменений пока подтверждается сборкой, линтом и ручной проверкой доменной логики.
- `npm run build` является обязательной базовой проверкой после значимых изменений; `lint` тоже обязателен, но его текущее состояние должно подтверждаться отдельным verification result.
- `CLAUDE.md` в репозитории генерируется через `ai-inst`; его нельзя считать свободно редактируемой основной памятью проекта.

## References

- file:/home/moonbreeze/forbidden-stars-companion/package.json
- file:/home/moonbreeze/forbidden-stars-companion/PLAN.md
- file:/home/moonbreeze/forbidden-stars-companion/instructions.local.md
- file:/home/moonbreeze/forbidden-stars-companion/CLAUDE.md
