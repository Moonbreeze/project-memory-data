---
date: 2026-03-17
project: english-assistant
topic: project-overview
registry_scope: project-overview
source: agent
status: active
---
# Canonical Doc

## Summary

AI-powered ассистент для преподавателя английского языка. Первая фича — генерация двухминутных подкастов-диалогов на заданную тему с контролем уровня, лексики и темпа.

## Guidance

- Целевая аудитория — преподаватель английского без IT-бэкграунда, UI должен быть интуитивным
- Монорепо (pnpm workspace): server + client + shared (path aliases)
- Бэкенд: Node.js (experimental-strip-types), Express
- Фронтенд: React + Redux Toolkit, Vite
- AI-провайдер: OpenAI (LLM-агент + TTS), на этапе разработки — моки
- Persistence: SQLite (better-sqlite3)
- Аудио: ffmpeg (fluent-ffmpeg) для склейки TTS-сегментов в MP3
- Деплой: Docker (multi-stage build), docker-compose, VPS, ssh + docker compose up
- Auth: пароль из .env + сессия. Публичные share-ссылки /share/:token (read-only, без авторизации)
- Два контекста доступа: авторизованный (полный) и публичный (только просмотр по share-ссылке)
- Транспортный слой абстрагирован — первая реализация HTTP/Express, архитектура позволяет подключить Telegram и др.
- Однопользовательский сценарий, но архитектура auth не завязана на одного пользователя
- Подкаст: диалог двух голосов, ~2 минуты, MP3, General American English
- Параметры подкаста: тема, ключевые слова (изучаемая лексика, буквально прозвучат), уровень CEFR (A1–C2), темп (скорость TTS)
- Базовый флоу: ввод параметров → генерация сценария → подтверждение/редактирование → TTS → MP3
- Опционально: быстрый режим без подтверждения, настройка системного промпта агента

## References

- decision:english-assistant:2026-03-17:tech-stack
- decision:english-assistant:2026-03-17:transport-abstraction
- decision:english-assistant:2026-03-17:podcast-generation-flow
- decision:english-assistant:2026-03-17:auth-and-sharing
- decision:english-assistant:2026-03-17:http-framework
- decision:english-assistant:2026-03-17:frontend-tooling
- decision:english-assistant:2026-03-17:shared-types-strategy
- decision:english-assistant:2026-03-17:persistence
- decision:english-assistant:2026-03-17:audio-assembly
- decision:english-assistant:2026-03-17:deployment
