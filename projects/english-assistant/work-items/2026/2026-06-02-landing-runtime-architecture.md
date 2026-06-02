---
date: 2026-06-02
recorded_at: 2026-06-02T16:47:42.658Z
project: english-assistant
topic: landing-runtime-architecture
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Зафиксировать целевую runtime-архитектуру лендинга и приложения на разных хостах в рамках одного репозитория и одного deploy-контура.

## Outcome

Определена целевая схема: отдельный landing-сервис для root-domain, текущий app-сервис для assistant subdomain, единый deploy через существующий webhook и docker compose.

## Provenance

- ad-hoc: Подготовка отдельного лендинга на root-domain при сохранении приложения на assistant subdomain с общим push-based deploy.

## Dependencies

- none

## Context

- none

## Verification

- Зафиксирована доменная схема: <root-domain> и www.<root-domain> ведут на landing, assistant.<root-domain> ведёт на app.
- Зафиксировано решение о выделении packages/landing как отдельного static bundle.
- Зафиксировано, где хранится и как сопровождается production reverse proxy configuration.

## Evidence

- session-note:english-assistant:2026-06-02:landing-runtime-architecture
- verification-result:english-assistant:2026-06-02:landing-runtime-architecture
