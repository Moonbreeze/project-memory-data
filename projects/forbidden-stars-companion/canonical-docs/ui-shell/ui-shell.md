---
date: 2026-06-02
recorded_at: 2026-06-02T11:41:48.482Z
project: forbidden-stars-companion
topic: ui-shell
registry_scope: ui-shell
source: agent
status: active
---
# Canonical Doc

## Summary

Приложение использует простую companion-оболочку с desktop sidebar, mobile bottom navigation и единой тёмной Warhammer-стилистикой.

## Guidance

- На desktop приложение использует фиксированный левый sidebar с навигацией, а на mobile — нижнюю навигацию; основной контент рендерится через `Outlet` внутри `Layout`.
- Навигация ограничена четырьмя пользовательскими разделами: ресурсы, бой, справочник и таймер.
- Визуальный язык проекта строится вокруг тёмного фона, золотых акцентов, gothic typography для заголовков и простых panel/button utility-классов в `index.css`.
- UI-оболочка должна поддерживать быстрый table-side usage: крупные действия, быстро читаемое состояние, минимум лишней вложенности и ясное разделение подсистем.
- При изменении оболочки сохранять характер companion-приложения: не превращать интерфейс в перегруженную админку или в board map simulator.

## References

- file:/home/moonbreeze/forbidden-stars-companion/src/components/Layout.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/components/Navigation.tsx
- file:/home/moonbreeze/forbidden-stars-companion/src/index.css
- file:/home/moonbreeze/forbidden-stars-companion/src/App.tsx
