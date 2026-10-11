---
date: 2026-10-08
recorded_at: 2026-10-08T05:37:31.059Z
project: vpn-reality
topic: temporary-direct-de-reality
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Временный прямой VLESS Reality endpoint DE:443 для мобильных и сторонних устройств на время недоступности Yandex relay.

## Outcome

Пользователь настроил fallback по инструкции и подтвердил успешное подключение; на DE появился listener 147.45.196.137:443, mtg остаётся на 10.66.0.2:3128. Ограничения проверки live config, firewall и клиентского egress явно зафиксированы в verification; rollback описан в session note.

## Provenance

- ad-hoc: Пользователь согласовал временный direct-DE доступ без SSH-туннелей на клиентских устройствах; административные действия выполнял самостоятельно с локальным вводом sudo-пароля.

## Dependencies

- none

## Context

- none

## Verification

- Отдельный direct inbound на DE:443 использует VLESS Reality Vision и www.cloudflare.com.
- UFW разрешает только временный публичный TCP 443, без расширения 8443/3128.
- Клиент из мобильной сети импортирует профиль и получает DE egress.
- Telegram работает через VPN с отключённым старым MTProto-прокси; rollback удаляет только временный inbound и его firewall rule.

## Evidence

- session-note:vpn-reality:2026-10-08:relay-outage-direct-de-fallback
- verification-result:vpn-reality:2026-10-08:relay-outage-direct-de-fallback
