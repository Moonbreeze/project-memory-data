---
date: 2026-03-17
project: english-assistant
topic: cost-estimates
source: agent
status: active
---
# Provider Note

## Overview

Оценка затрат на инфраструктуру и API для проекта english-assistant. Цены ориентировочные, актуальны на март 2026. Базовый сценарий: 5 подкастов/день по ~2 минуты.

## Constraints

- OpenAI TTS (tts-1): $15/1M символов. 1 диалог (~1800 симв.) = $0.027. 5/день = $0.14. ~$4/мес.
- OpenAI TTS (tts-1-hd): $30/1M символов. ~$8/мес при 5/день.
- OpenAI LLM (gpt-4o): $2.50/1M input, $10/1M output. 1 диалог (~500 input + ~450 output токенов) = $0.006. ~$1/мес.
- OpenAI итого: ~$5/мес (tts-1) или ~$9/мес (tts-1-hd) при 5 подкастах/день.
- При 20 подкастах/день: ~$20/мес (tts-1).
- VPS минимум: 1 vCPU, 1 GB RAM, 20 GB SSD. Комфортно: 2 vCPU, 2 GB RAM, 40 GB SSD.
- Хранилище аудио: ~300 MB/мес (~2 MB на MP3 × 5/день), ~3.6 GB/год.
- Hetzner CX22 (2 vCPU, 4 GB, 40 GB): ~€4/мес. CX11 (1 vCPU, 2 GB, 20 GB): ~€3.5/мес.
- DigitalOcean Basic 1 vCPU/1 GB/25 GB: ~$6/мес. 1 vCPU/2 GB/50 GB: ~$12/мес.
- Timeweb Cloud 1 vCPU/1 GB/15 GB: ~₽400/мес. Selectel 1 vCPU/1 GB/10 GB: ~₽500/мес.

## Guidance

- Бюджетный вариант (Hetzner + tts-1): ~$9/мес
- Средний вариант (DO + tts-1-hd): ~$15/мес
- С запасом (DO 2 GB + tts-1-hd, 20 подкастов/день): ~$32/мес
- Основная статья расходов — TTS, не LLM
- Цены ориентировочные, актуальны на март 2026 — перепроверять перед закупкой
- Для российских провайдеров учитывать возможные ограничения доступа к OpenAI API
