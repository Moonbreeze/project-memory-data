---
date: 2026-04-19
recorded_at: 2026-04-19T16:50:35.550Z
project: english-assistant
topic: openai
source: agent
status: active
---
# Provider Note

## Overview

OpenAI используется в podcast pipeline для генерации сценария и text-to-speech.

## Constraints

- API billing для platform.openai.com отделён от ChatGPT Plus; для работы требуется отдельный API key и включённый platform billing.
- Текущая интеграция использует один OPENAI_API_KEY и для script generation, и для TTS.
- TTS сейчас пишет итоговый MP3 в локальный audio path контейнера; внешний storage ещё не подключён.

## Guidance

- Для script generation используется gpt-5-mini через Responses API со structured JSON output.
- Для TTS используется gpt-4o-mini-tts через audio/speech; текущий voice mapping: host=cedar, guest=marin.
- Обязательные env для production: OPENAI_API_KEY; рекомендуемые явные env: OPENAI_SCRIPT_MODEL, OPENAI_TTS_MODEL, OPENAI_TTS_HOST_VOICE, OPENAI_TTS_GUEST_VOICE.
- При изменении voice/model defaults сначала проверять локальный synthesize smoke, затем production deploy smoke.
