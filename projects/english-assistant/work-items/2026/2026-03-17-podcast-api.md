---
date: 2026-03-17
recorded_at: 2026-03-17T00:00:00.000Z
project: english-assistant
topic: podcast-api
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

REST-эндпоинты подкаста: создать (POST), получить сценарий (GET), подтвердить/отредактировать (PATCH), запустить синтез (POST), скачать MP3 (GET). Оркестратор podcastGenerator.

## Outcome

Полный API-флоу от создания подкаста до скачивания MP3 работает на моках.

## Provenance

- decision:english-assistant:2026-03-17:podcast-generation-flow

## Dependencies

- work-item:english-assistant:2026-03-17:podcast-script-generation
- work-item:english-assistant:2026-03-17:podcast-tts
- work-item:english-assistant:2026-03-17:bootstrap-db

## Context

- none

## Verification

- Полный цикл через curl/httpie
- Статусы жизненного цикла корректно меняются
- MP3 скачивается

## Evidence

- session-note:english-assistant:2026-03-21:podcast-api
- verification-result:english-assistant:2026-03-21:podcast-api
