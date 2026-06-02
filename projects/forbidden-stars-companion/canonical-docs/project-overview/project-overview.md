---
date: 2026-06-02
recorded_at: 2026-06-02T11:41:09.720Z
project: forbidden-stars-companion
topic: project-overview
registry_scope: project-overview
source: agent
status: active
---
# Canonical Doc

## Summary

Forbidden Stars Companion — локальное companion-приложение для живой партии, сосредоточенное на бою, таймерах и планировании ресурсов, а не на полном цифровом трекинге всей игры.

## Guidance

- Проект предназначен для использования рядом с физической партией в Forbidden Stars как вспомогательный инструмент, а не как цифровая замена настольной игры.
- Текущие центральные подсистемы приложения: помощь и симуляция в бою, отслеживание состояния боевых колод игроков, планирование ресурсов на ход и шахматные таймеры.
- Приложение работает как клиентский React/Vite SPA без обязательного бэкенда, без обязательного постоянного хранения и без серверной логики.
- Сущность партии допустима как агрегат пользовательского состояния приложения, прежде всего для таймеров и текущего состояния боевых колод игроков.
- Целевое развитие проекта должно усиливать полезность за игровым столом и скорость принятия решений, а не расширять продукт в сторону полного трекера карты, приказов и всех состояний партии.

## References

- pdf:/home/moonbreeze/Forbidden Stars - Rules Reference.pdf
- pdf:/home/moonbreeze/forbidden_stars_faq_1.1.pdf
- pdf:/home/moonbreeze/Forbidden_Stars_Database.pdf
- file:/home/moonbreeze/forbidden-stars-companion/src/App.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/pages/CombatPage.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/pages/ResourcesPage.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/pages/TimerPage.tsx
