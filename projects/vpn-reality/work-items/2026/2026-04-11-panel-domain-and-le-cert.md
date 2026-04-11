---
date: 2026-04-11
recorded_at: 2026-04-11T16:25:05.473Z
project: vpn-reality
topic: panel-domain-and-le-cert
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Привязать домен к 3x-ui панели и выпустить Let's Encrypt сертификат, чтобы перестать полагаться на SSH-туннель.

## Outcome

Панель доступна по HTTPS на отдельном поддомене с TLS; SSH-туннель остаётся резервным доступом.

## Provenance

- decision:vpn-reality:2026-04-11:ssh-tunnel-over-le

## Dependencies

- none

## Context

- none

## Verification

- Домен резолвится в 147.45.196.137.
- curl https://<panel-domain>/<basePath>/ возвращает 200 с валидным LE-сертификатом.
- ufw открывает 443 только для панели-поддомена или панель слушает на отдельном порту.

## Evidence

- none
