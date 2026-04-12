---
date: 2026-04-11
recorded_at: 2026-04-11T16:25:05.473Z
project: vpn-reality
topic: panel-domain-and-le-cert
source: agent
status: archived
work_item_state: canceled
---
# Work Item

## Summary

Отменён как устаревший по скоупу. Исходная формулировка («привязать домен к 3x-ui панели и выпустить LE») смешивала два независимых use-case: админ-доступ к web UI (закрыт SSH-туннелем, decision ssh-tunnel-over-le валиден) и публичный subscription-endpoint для клиентов. Решение profile-file-over-subscription-url от 2026-04-11 закрыло потребность в публичном endpoint файловой доставкой профиля. Домен не покупается, :80/:8443 остаются закрыты, LE не настраивается. При появлении реального триггера (user-base ≥5 устройств ИЛИ квартальная ротация ключей Reality) создать новый work-item с узким скоупом «TLS только для subscription-server, панель UI остаётся на SSH-туннеле».

## Outcome

Work-item закрыт как canceled. Никаких изменений в инфраструктуре не делается. SSH-туннель остаётся единственным способом админить панель. Subscription-server 3x-ui (:2096) остаётся закрытым в ufw. Домен для проекта не регистрируется.

## Provenance

- decision:vpn-reality:2026-04-11:ssh-tunnel-over-le

## Dependencies

- none

## Context

- decision:vpn-reality:2026-04-11:profile-file-over-subscription-url
- decision:vpn-reality:2026-04-11:ssh-tunnel-over-le

## Verification

- Work-item помечен canceled и archived.
- В decision profile-file-over-subscription-url зафиксированы триггеры для пересоздания.

## Evidence

- none
