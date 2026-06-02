---
date: 2026-06-02
recorded_at: 2026-06-02T16:58:09.654Z
project: english-assistant
topic: landing-runtime-architecture
source: agent
status: active
---
# Decision

## Context

Подготовка отдельного production landing на root-domain при сохранении текущего приложения на assistant subdomain в рамках одного репозитория и существующего webhook-based deploy flow. В репозитории на момент решения есть один compose service `app`, который одновременно обслуживает API/backend и собранный client bundle, а `deploy.sh` уже выполняет общий `docker compose up -d --build`.

## Decision

Целевая runtime-архитектура строится как split-host topology: отдельный `landing` service обслуживает `<root-domain>`, `www.<root-domain>` редиректится на канонический root host, а текущий `app` service продолжает обслуживать `assistant.<root-domain>`. Оба сервиса разворачиваются в одном compose-проекте и обновляются одним webhook-triggered deploy. Production reverse proxy configuration для публичных hostnames хранится в репозитории в `deploy/reverse-proxy/` и меняется вместе с topology-изменениями.

## Consequences

- Следующий этап должен создать `packages/landing` как отдельный static bundle и добавить отдельный compose service `landing`.
- `app` сохраняет ответственность за backend routes, auth/session behavior, share endpoints и storage volumes; landing не получает доступ к SQLite и audio storage.
- Публичная маршрутизация и canonical-host behavior становятся versioned артефактами репозитория, а не внешней неявной настройкой VPS.
- Финальный production smoke должен проверять root-domain, `www` redirect и `assistant` host после общего push-triggered deploy.

## Stable Guidance Review

- Outcome: reviewed-no-change
- Summary: Reviewed current stable guidance and determined no update was required.
