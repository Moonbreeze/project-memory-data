---
date: 2026-10-08
recorded_at: 2026-10-08T05:34:44.197Z
project: vpn-reality
topic: relay-unreachable-vpn-mtg
source: agent
status: active
work_item_state: blocked
---
# Work Item

## Summary

Общий Yandex relay недоступен с DE, оба relay-first контура не работают; временный прямой доступ на DE восстановлен пользователем.

## Outcome

Восстановлены relay:443 и relay:9443, проверены VPN egress и Telegram connection; устройства возвращены на relay-first и временный direct-DE fallback удалён без изменения закрытых backend-портов.

## Provenance

- ad-hoc: Пользователь находится на DE по SSH, сообщил отказ обоих клиентских контуров и проблемы у Yandex Cloud. Диагностика подтверждает недоступность relay с DE, причина на стороне облака независимо не подтверждена.

## Dependencies

- none

## Context

- none

## Verification

- TCP-доступность relay 178.154.193.39:22/443/9443 с DE.
- Свежий WireGuard handshake, доступность 10.66.0.1 и HAProxy backend UP.
- VPN через relay показывает DE egress; Telegram подключается через relay:9443.
- После возвращения устройств на relay-first отключён/удалён temporary-direct-de inbound и только его UFW allow; DE backend 3128 остаётся приватным и backhaul 8443 ограничен relay.

## Evidence

- session-note:vpn-reality:2026-10-08:relay-outage-direct-de-fallback
- verification-result:vpn-reality:2026-10-08:relay-outage-direct-de-fallback
