---
date: 2026-03-17
project: english-assistant
topic: bootstrap-server
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Express-сервер: базовая структура (transport/, services/, ai/, config/), health-check эндпоинт, запуск через node --experimental-strip-types.

## Outcome

Сервер запускается, отвечает на GET /health.

## Provenance

- decision:english-assistant:2026-03-17:http-framework

## Dependencies

- work-item:english-assistant:2026-03-17:bootstrap-monorepo

## Context

- none

## Verification

- pnpm dev запускает сервер
- GET /health возвращает 200
- Структура директорий сервера соответствует плану

## Evidence

- none
