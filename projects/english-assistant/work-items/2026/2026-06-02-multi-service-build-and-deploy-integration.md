---
date: 2026-06-02
recorded_at: 2026-06-02T16:47:42.685Z
project: english-assistant
topic: multi-service-build-and-deploy-integration
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Встроить лендинг в Docker и deploy-контур так, чтобы push в репозиторий пересобирал и приложение, и лендинг без ручных шагов.

## Outcome

Dockerfile и docker-compose поддерживают два сервиса, а текущий deploy.sh по push разворачивает оба артефакта в одном процессе.

## Provenance

- ad-hoc: Интеграция лендинга в существующий webhook-based deployment flow.

## Dependencies

- work-item:english-assistant:2026-06-02:landing-package-scaffold-and-shell

## Context

- none

## Verification

- docker compose up -d --build поднимает и landing, и app.
- Изменения в packages/landing попадают в build и deployment flow.
- Текущее приложение на assistant subdomain не ломается после разделения на два сервиса.
- Локальный smoke подтверждает старт обоих сервисов.

## Evidence

- none
