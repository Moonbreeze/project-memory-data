---
date: 2026-03-17
recorded_at: 2026-03-17T00:00:00.000Z
project: english-assistant
topic: podcast-tts
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Сервис TTS: интерфейс SpeechSynthesizer + мок. Склейка аудиосегментов через fluent-ffmpeg в MP3.

## Outcome

Мок генерирует аудиосегменты, assembler склеивает их в один MP3.

## Provenance

- decision:english-assistant:2026-03-17:audio-assembly

## Dependencies

- work-item:english-assistant:2026-03-17:podcast-domain-types
- work-item:english-assistant:2026-03-17:bootstrap-server

## Context

- none

## Verification

- Мок генерирует аудиосегменты
- ffmpeg склеивает сегменты в один MP3
- Результат — валидный MP3-файл

## Evidence

- session-note:english-assistant:2026-03-21:tts-implementation
- verification-result:english-assistant:2026-03-21:tts-tests
