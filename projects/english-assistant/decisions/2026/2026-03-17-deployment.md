---
date: 2026-03-17
project: english-assistant
topic: deployment
source: user
status: active
---
# Decision

## Context

Деплой на VPS, нужна простая и воспроизводимая процедура. Проект имеет системную зависимость (ffmpeg), что усложняет ручную установку.

## Decision

Docker с multi-stage build. Stage 1: Vite build фронтенда. Stage 2: Node.js + ffmpeg + собранная статика + серверный код. docker-compose.yml с volumes для SQLite и аудиофайлов. Деплой: ssh + docker compose up -d --build.

## Consequences

- Один контейнер — просто для однопользовательского сервиса
- ffmpeg в образе, не нужно ставить на хост
- Volumes для данных — переживают пересборку
- Нет CI/CD на старте, ручной деплой через ssh
- При масштабировании можно разнести на отдельные контейнеры
