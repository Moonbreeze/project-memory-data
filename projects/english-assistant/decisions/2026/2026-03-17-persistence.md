---
date: 2026-03-17
project: english-assistant
topic: persistence
source: user
status: active
---
# Decision

## Context

Нужно хранить состояние подкастов (жизненный цикл draft→completed), сессии, share-токены. Однопользовательский сценарий, серверный деплой в Docker.

## Decision

SQLite через better-sqlite3. Файл БД на Docker volume.

## Consequences

- Нет внешних зависимостей (БД в файле)
- Синхронный API better-sqlite3 упрощает код
- При переходе к многопользовательскому режиму SQLite может стать узким местом — но для одного пользователя более чем достаточно
- Миграции схемы нужно продумать (можно простой SQL-файл на старте)
