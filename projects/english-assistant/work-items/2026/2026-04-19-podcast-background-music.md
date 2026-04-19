---
date: 2026-04-19
recorded_at: 2026-04-19T17:01:44.486Z
project: english-assistant
topic: podcast-background-music
source: user
status: active
work_item_state: open
---
# Work Item

## Summary

Добавить фоновую музыку как отдельный audio layer для podcast output, не ухудшая разборчивость речи.

## Outcome

Подкаст может собираться не только из speech segments, но и с музыкальным слоем: как минимум intro/outro sting или тихая подложка, с контролируемой громкостью и предсказуемым runtime behavior. Решение явно фиксирует, это default behavior или optional toggle.

## Provenance

- ad-hoc: Requested during the April 19, 2026 discussion as a follow-up item after improving the core podcast result itself.

## Dependencies

- work-item:english-assistant:2026-04-19:podcast-dialogue-quality

## Context

- none

## Verification

- Финальный MP3 может включать музыкальный слой без поломки существующего speech assembly pipeline.
- Музыка не мешает разборчивости речи: уровень фона стабильно ниже речи, а на участках с голосом не возникает заметного masking.
- Для mixing strategy определены конкретные правила: gain, ducking при необходимости, intro/outro behavior.
- Источник музыкальных ассетов, ограничения использования и runtime assumptions зафиксированы явно.
- Если музыка делается опциональной, UI/API корректно управляют этим режимом без regressions.

## Evidence

- none
