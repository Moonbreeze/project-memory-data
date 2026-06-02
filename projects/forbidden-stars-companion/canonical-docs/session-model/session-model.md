---
date: 2026-06-02
recorded_at: 2026-06-02T11:41:48.467Z
project: forbidden-stars-companion
topic: session-model
registry_scope: session-model
source: agent
status: active
---
# Canonical Doc

## Summary

Сессия приложения представляет живую партию как открытое общее состояние игроков, ресурсов, текущих боевых колод и настроек таймера, но не как полный трек board state.

## Guidance

- Сессия хранит игроков, выбранные фракции, текущий раунд, первого игрока, ресурсы, активы, территории, objective tokens, боевые колоды и купленные апгрейды.
- Текущая сессионная модель нужна для practical companion-функций и не обязана покрывать все сущности настольной партии.
- Сущность партии допустимо развивать как контейнер для совместного состояния нескольких устройств, если это поможет live-play сценарию без расширения scope до полного трекера карты и приказов.
- Все данные сессии в текущей реализации открыты для стола; обязательная модель приватной информации игроков отсутствует.
- Персистентность, импорт и экспорт не являются обязательной частью текущей модели сессии.

## References

- file:/home/moonbreeze/forbidden-stars-companion/src/stores/sessionStore.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/App.tsx
- chat:user-direction:2026-06-02:session-vision
