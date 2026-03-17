---
date: 2026-03-17
project: english-assistant
topic: audio-assembly
source: user
status: active
---
# Decision

## Context

TTS генерирует отдельные аудиосегменты для каждого голоса/реплики. Нужно склеить их в один MP3-файл.

## Decision

ffmpeg через fluent-ffmpeg для склейки аудиосегментов в итоговый MP3. ffmpeg устанавливается в Docker-образ.

## Consequences

- Системная зависимость ffmpeg — решается через Docker
- fluent-ffmpeg — зрелая обёртка, хорошо документирована
- Возможность добавить постобработку (нормализация громкости, паузы между репликами)
