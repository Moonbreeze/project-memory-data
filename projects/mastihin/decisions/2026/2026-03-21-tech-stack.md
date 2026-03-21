---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: mastihin
topic: tech-stack
source: user
status: active
---
# Decision

## Context

Выбор стека для MVP арт-платформы. Один разработчик, бывший бэкендер, знает TS и NestJS. Хочет разнести фронт и бэк.

## Decision

Frontend: React + Vite + TypeScript (простая структура по фичам, без FSD). Backend: NestJS + TypeScript. БД: PostgreSQL (на VPS). Хранение: S3-совместимое (Yandex/Selectel). Хостинг: VPS в России. Монорепо: pnpm workspaces, общие типы в отдельном пакете.

## Consequences

- Два отдельных деплоя (фронт + бэк)
- SSR отсутствует — SEO через prerender/meta-tags
- Общие типы требуют отдельного пакета в монорепо
- NestJS даёт структуру из коробки

## Stable Guidance Review

- Outcome: bootstrap-exempt
- Summary: Bootstrap-style decision write where no prior stable-guidance surface existed yet.
- Note: Первые решения проекта.
