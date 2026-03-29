---
date: 2026-03-17
recorded_at: 2026-03-17T00:00:00.000Z
project: english-assistant
topic: podcast-ui
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

UI подкаста: форма ввода параметров (тема, ключевые слова, уровень CEFR, темп), отображение/редактирование сценария, подтверждение, прогресс синтеза, скачивание MP3.

## Outcome

Пользователь проходит полный флоу в браузере от ввода параметров до скачивания MP3.

## Provenance

- decision:english-assistant:2026-03-17:podcast-generation-flow

## Dependencies

- work-item:english-assistant:2026-03-17:podcast-api
- work-item:english-assistant:2026-03-17:bootstrap-client

## Context

- none

## Verification

- Форма валидирует ввод
- Сценарий отображается и редактируется
- MP3 скачивается через браузер

## Evidence

- session-note:english-assistant:2026-03-29:podcast-ui
- verification-result:english-assistant:2026-03-29:podcast-ui
