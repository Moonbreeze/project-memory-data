---
date: 2026-03-17
recorded_at: 2026-03-17T00:00:00.000Z
project: english-assistant
topic: deploy-webhook
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

deploy/: webhook-listener (валидация GitHub secret) и testable deploy.sh для локально проверяемого trigger flow до появления VPS; systemd unit и VPS-документация готовятся заранее, а финальная ops-проверка откладывается до появления целевого хоста.

## Outcome

Локально подтверждается цепочка GitHub-style webhook -> secret validation -> запуск deploy flow, а финальная проверка systemd и reboot/autostart выполняется отдельным последним этапом после появления VPS.

## Provenance

- decision:english-assistant:2026-03-17:deploy-via-git

## Dependencies

- work-item:english-assistant:2026-03-17:docker

## Context

- none

## Verification

- Webhook listener локально принимает запрос и корректно валидирует GitHub secret
- deploy.sh выполняется в локально тестируемом режиме и подтверждает ожидаемую последовательность backup + update + rebuild
- Ручной локальный trigger webhook -> listener -> deploy flow проходит end-to-end без готового VPS
- systemd unit и инструкция по установке подготовлены, но автостарт после reboot помечен как отложенная проверка до появления реального VPS

## Evidence

- none
