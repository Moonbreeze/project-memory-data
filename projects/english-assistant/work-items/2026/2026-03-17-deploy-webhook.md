---
date: 2026-03-17
project: english-assistant
topic: deploy-webhook
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

deploy/: webhook-listener (валидация GitHub secret), deploy.sh (backup БД + git pull + docker compose up), systemd unit, документация по настройке VPS.

## Outcome

Push в GitHub автоматически триггерит пересборку и деплой на VPS.

## Provenance

- decision:english-assistant:2026-03-17:deploy-via-git

## Dependencies

- work-item:english-assistant:2026-03-17:docker

## Context

- none

## Verification

- Webhook приходит, listener валидирует secret
- deploy.sh выполняет backup + rebuild
- systemd автостарт listener после ребута

## Evidence

- none
