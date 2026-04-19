---
date: 2026-04-19
recorded_at: 2026-04-19T13:53:05.142Z
project: english-assistant
topic: podcast-audio-storage
source: user
status: active
work_item_state: open
---
# Work Item

## Summary

Вынести хранение сгенерированного аудио подкастов из локального AUDIO_DIR во внешнее storage.

## Outcome

Синтезированное аудио подкастов сохраняется и читается через внешний storage adapter вместо локального файлового пути, а backend имеет ясную стратегию URL/access для podcast audio и share endpoints.

## Provenance

- ad-hoc: Requested by the user after reviewing the active backlog and identifying that podcast audio is still stored in local AUDIO_DIR without external storage integration.

## Dependencies

- none

## Context

- none

## Verification

- После synthesize аудиофайл публикуется во внешний storage и остаётся доступен через ожидаемый backend access path или URL.
- Podcast audio и shared audio endpoints продолжают корректно работать после перехода с локального AUDIO_DIR на storage adapter.
- Конфигурация storage provider, expected runtime behavior и deploy assumptions явно зафиксированы для production use.

## Evidence

- none
