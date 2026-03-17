---
date: 2026-03-17
project: english-assistant
topic: shared-types-strategy
source: user
status: active
---
# Decision

## Context

Общие типы между клиентом и сервером (API-контракты, доменные модели). Нужно решить — отдельный пакет или path aliases.

## Decision

На старте — path aliases (tsconfig paths) на общую директорию shared/. Выделение в отдельный пакет монорепо при необходимости.

## Consequences

- Минимум конфигурации на старте
- Нет отдельного package.json и build-шага для shared
- При выделении в пакет потребуется рефакторинг импортов
