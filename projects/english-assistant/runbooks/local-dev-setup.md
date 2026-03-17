---
date: 2026-03-17
project: english-assistant
topic: local-dev-setup
source: agent
status: draft
---
# Runbook

## Purpose

Локальный запуск проекта для разработки. Будет дополнен после инициализации монорепо.

## Procedure

- Клонировать репозиторий
- Установить Node.js >= 22.6.0
- Установить pnpm
- pnpm install в корне монорепо
- Скопировать .env.example в .env, заполнить переменные
- pnpm dev — запуск в режиме разработки

## Verification

- pnpm dev запускается без ошибок
- Фронтенд доступен в браузере
- Бэкенд отвечает на health-check
