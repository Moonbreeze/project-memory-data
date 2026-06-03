---
date: 2026-06-03
recorded_at: 2026-06-03T09:42:12.574Z
project: english-assistant
topic: landing-package-scaffold-and-shell
source: agent
status: active
---
# Session Note

## Summary

Собран отдельный пакет лендинга `packages/landing` с первым production-ready shell и CTA в приложение.

## Actions

- Создан новый workspace-пакет `packages/landing` с Vite scripts и базовой конфигурацией.
- Добавлен первый лендинг с hero, value proposition, CTA, favicon и SEO/Open Graph meta tags.
- Реализован runtime helper для CTA через `VITE_ASSISTANT_URL` с fallback на `assistant.<root-domain>` и `localhost` для локальной разработки.
- Проверена production-сборка командой `pnpm --filter @english-assistant/landing build`.
- Для ручного просмотра лендинг временно поднимался на VPS через Vite dev server и затем был остановлен.

## Follow-up

- Интегрировать `landing` в `docker-compose`, Docker build и webhook deploy в work-item `multi-service-build-and-deploy-integration`.
- Настроить production reverse proxy routing для root-domain, `www` и `assistant` в work-item `production-domain-routing-and-smoke`.
