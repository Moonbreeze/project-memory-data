---
date: 2026-06-02
recorded_at: 2026-06-02T11:42:59.332Z
project: forbidden-stars-companion
topic: timer-system
registry_scope: timer-system
source: agent
status: active
---
# Canonical Doc

## Summary

Таймерная подсистема реализует table-side chess-clock для стратегических и боевых решений и должна оставаться простой служебной функцией companion-приложения.

## Guidance

- Приложение поддерживает два режима таймера: стратегический и боевой, каждый со своим временем хода и банком резерва.
- Таймер предназначен для живой партии и не зависит от полной модели игрового состояния.
- Текущее состояние таймера включает число игроков, текущего игрока, время текущего хода, reserve time и состояние запуска.
- Если в будущем появится синхронизация устройств, таймер и привязка к сущности партии являются естественным кандидатом на совместное состояние.
- Таймер не должен усложняться логикой всех фаз партии; его задача — поддерживать темп и дисциплину принятия решений за столом.

## References

- file:/home/moonbreeze/forbidden-stars-companion/src/pages/TimerPage.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/stores/timerStore.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/App.tsx
