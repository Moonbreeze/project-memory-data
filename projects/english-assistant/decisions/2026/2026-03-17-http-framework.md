---
date: 2026-03-17
project: english-assistant
topic: http-framework
source: user
status: active
---
# Decision

## Context

Выбор HTTP-фреймворка для бэкенда. Однопользовательский сценарий, производительность не критична, важна простота.

## Decision

Express как HTTP-фреймворк. Простой, хорошо знакомый, достаточный для однопользовательского сервиса.

## Consequences

- Стандартный middleware-паттерн для auth, error handling и т.д.
- Большая экосистема middleware
- В продакшене Express также отдаёт собранную Vite-статику фронтенда
