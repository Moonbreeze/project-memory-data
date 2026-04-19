---
date: 2026-03-29
recorded_at: 2026-03-29T09:58:16.179Z
project: english-assistant
topic: deploy-webhook-vps-rollout
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Развернуть готовый webhook listener на реальном VPS: подготовить environment/config, установить systemd unit, настроить GitHub webhook и подтвердить end-to-end production trigger.

## Outcome

Реальный push в GitHub доходит до VPS listener, проходит secret validation, запускает deploy flow через systemd-managed сервис, а автоподъём после reboot подтверждён на целевом хосте.

## Provenance

- session-note:english-assistant:2026-03-29:deploy-webhook

## Dependencies

- work-item:english-assistant:2026-03-17:docker

## Context

- none

## Verification

- Listener установлен и запускается на VPS через systemd с корректным environment file.
- GitHub webhook настроен на публичный endpoint VPS и реальный signed push event достигает listener.
- Deploy flow на VPS выполняет backup + update + docker compose rebuild на целевом хосте.
- После reboot VPS listener автоматически поднимается и продолжает принимать webhook-запросы.

## Evidence

- session-note:english-assistant:2026-04-19:deploy-webhook-vps-rollout
- verification-result:english-assistant:2026-04-19:deploy-webhook-vps-rollout
