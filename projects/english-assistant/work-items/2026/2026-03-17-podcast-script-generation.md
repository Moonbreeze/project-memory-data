---
date: 2026-03-17
project: english-assistant
topic: podcast-script-generation
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Сервис генерации сценария: интерфейс ScriptGenerator + мок-реализация. Промпт для LLM. Валидация наличия ключевых слов в результате.

## Outcome

Мок генерирует сценарий-диалог с заданными ключевыми словами, соответствующий доменным типам.

## Provenance

- decision:english-assistant:2026-03-17:podcast-generation-flow

## Dependencies

- work-item:english-assistant:2026-03-17:podcast-domain-types
- work-item:english-assistant:2026-03-17:bootstrap-server

## Context

- none

## Verification

- Мок возвращает валидный сценарий
- Ключевые слова присутствуют в сценарии
- Интерфейс позволяет подменить мок на OpenAI

## Evidence

- none
