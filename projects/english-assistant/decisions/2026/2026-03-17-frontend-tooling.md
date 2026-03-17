---
date: 2026-03-17
project: english-assistant
topic: frontend-tooling
source: user
status: active
---
# Decision

## Context

Выбор сборщика для React-фронтенда в монорепо.

## Decision

Vite как сборщик фронтенда. Быстрый dev-сервер, простая конфигурация, нативная поддержка TypeScript и React.

## Consequences

- Dev-режим: Vite dev server с proxy на Express
- Prod-режим: Vite build → статика, раздаётся Express
