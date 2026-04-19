---
date: 2026-04-19
recorded_at: 2026-04-19T13:53:05.216Z
project: english-assistant
topic: openai-podcast-generation
source: user
status: active
work_item_state: open
---
# Work Item

## Summary

Подключить реальную интеграцию OpenAI для генерации сценария подкаста вместо mockScriptGenerator.

## Outcome

Backend генерирует сценарий подкаста через реальный OpenAI provider, валидирует required config/API key, корректно обрабатывает provider failures и сохраняет production-ready script без зависимости от mock script generator.

## Provenance

- ad-hoc: Requested by the user after reviewing the active backlog and identifying that production OpenAI integration for podcast generation is not yet connected.

## Dependencies

- none

## Context

- none

## Verification

- Создание подкаста приводит к генерации сценария через реальный OpenAI provider или через изолированную проверку production adapter без использования mockScriptGenerator.
- Конфигурационный контракт для OpenAI (env vars, required secrets, model selection) явно определён и проверяем при запуске.
- Текущий podcast workflow не получает regressions в status transitions, error handling и API responses.

## Evidence

- none
