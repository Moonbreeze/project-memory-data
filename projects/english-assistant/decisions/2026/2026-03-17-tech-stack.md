---
date: 2026-03-17
project: english-assistant
topic: tech-stack
source: user
status: active
---
# Decision

## Context

Выбор технологического стека для нового проекта — AI-ассистента для преподавателя английского. Нужен веб-сервис с UI, пригодным для пользователя без IT-бэкграунда. Проект будет расширяться новыми фичами.

## Decision

Монорепо на pnpm. Бэкенд: Node.js с нативным запуском TypeScript (experimental-strip-types). Фронтенд: React + Redux Toolkit. AI-провайдер: OpenAI (LLM + TTS). Деплой: VPS.

## Consequences

- pnpm workspace для управления пакетами монорепо
- Минимальная версия Node.js >= 22.6.0 (experimental-strip-types)
- Зависимость от OpenAI API — нужна абстракция для возможной смены провайдера
- Разработка на моках OpenAI до получения ключей
- React + Redux Toolkit определяет фронтенд-экосистему (роутер, сборщик и т.д.)
