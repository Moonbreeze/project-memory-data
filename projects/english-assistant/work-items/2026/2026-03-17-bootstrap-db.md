---
date: 2026-03-17
project: english-assistant
topic: bootstrap-db
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

SQLite через better-sqlite3: инициализация, схема, простые SQL-миграции.

## Outcome

БД создаётся при старте, схема применяется, сервис доступен в DI.

## Provenance

- decision:english-assistant:2026-03-17:persistence

## Dependencies

- work-item:english-assistant:2026-03-17:bootstrap-server

## Context

- none

## Verification

- БД файл создаётся при старте
- Миграции применяются
- Базовые CRUD-операции работают

## Evidence

- none
