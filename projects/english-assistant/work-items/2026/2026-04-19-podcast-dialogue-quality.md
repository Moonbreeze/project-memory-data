---
date: 2026-04-19
recorded_at: 2026-04-19T17:01:36.609Z
project: english-assistant
topic: podcast-dialogue-quality
source: user
status: active
work_item_state: open
---
# Work Item

## Summary

Сделать центральный результат подкаста заметно сильнее: добавить настраиваемую продолжительность с дефолтом около 3 минут, сделать диалог живым, ввести имена спикеров и улучшить expressive delivery для TTS.

## Outcome

Новый подкаст по умолчанию звучит как полноценный разговор на несколько минут, а продолжительность остаётся настраиваемым параметром для разных учеников и сценариев использования. У спикеров есть устойчивые identity/name-role attributes, сценарий содержит вопросы, follow-up, согласие или несогласие и противоположные точки зрения, а TTS получает достаточно metadata или instruction depth, чтобы озвучка звучала менее плоско и монотонно.

## Provenance

- ad-hoc: Requested during the April 19, 2026 discussion about improving the core podcast result: configurable duration with a default around 3 minutes, stronger conversational dynamics, named speakers, and more expressive speech delivery without introducing background music yet.

## Dependencies

- none

## Context

- none

## Verification

- В API, UI или доменной модели есть явный duration control для подкаста, а отсутствие явной настройки использует дефолт около 3 минут.
- Сгенерированный по умолчанию сценарий без ручных правок обычно даёт подкаст порядка 3 минут, а не около 1 минуты.
- В сгенерированном диалоге есть признаки реальной беседы: вопросы между спикерами, реакции на сказанное, согласие или несогласие, и обсуждение хотя бы двух точек зрения.
- В данных подкаста и UI у спикеров есть имена, а не только host и guest.
- Синтез использует расширенную delivery-информацию или более сильные TTS instructions, и итоговая озвучка субъективно звучит более эмоционально и менее монотонно.
- Create, review, confirm и synthesize flow остаются рабочими после расширения модели сценария, speaker metadata и duration control.

## Evidence

- none
