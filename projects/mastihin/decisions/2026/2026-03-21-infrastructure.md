---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: mastihin
topic: infrastructure
source: user
status: active
---
# Decision

## Context

Выбор инфраструктуры. Хостинг в России для избежания блокировок, только российские решения по хранению.

## Decision

VPS в России (Timeweb Cloud / Selectel), ~2 vCPU / 4 GB RAM / 40 GB SSD. S3 — Yandex Object Storage или Selectel. PostgreSQL на том же VPS, бэкапы pg_dump на S3. Бюджет: ~1000-1500 руб/мес на старте. Ресайз изображений на сервере при загрузке (оригинал + 2-3 превью). Отдача изображений напрямую с S3. CDN добавить при росте.

## Consequences

- Всё на одном VPS на старте — просто, но единая точка отказа
- При росте (1000+ пользователей) — вынос БД в managed, добавление CDN, ~5000-8000 руб/мес
- Российский хостинг избавляет от проблем с блокировками

## Stable Guidance Review

- Outcome: bootstrap-exempt
- Summary: Bootstrap-style decision write where no prior stable-guidance surface existed yet.
- Note: Первые решения проекта.
