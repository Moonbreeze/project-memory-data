---
date: 2026-10-11
recorded_at: 2026-10-11T20:40:55.459Z
project: vpn-reality
topic: retire-temporary-direct-de-after-vdsina
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

После 24-часового периода наблюдения удалить только временный direct-DE Reality fallback, сохранив решение по старому Yandex peer отдельным.

## Outcome

Temporary direct-DE inbound на 147.45.196.137:443 и только его UFW rule удалены после стабильной работы VDSina relay; старые Yandex peer/rules не затронуты без отдельного решения.

## Provenance

- session-note:vpn-reality:2026-10-11:vdsina-ru-relay-client-validation

## Dependencies

- none

## Context

- none

## Verification

- В течение 24 часов новый VDSina VPN и Telegram relay не показывают повторяющихся отказов.
- Перед cleanup повторно подтверждены managed services, свежий WireGuard handshake и DE backend paths на ruhop.
- В 3x-ui отключён/удалён только temporary direct-DE inbound 147.45.196.137:443; DE backhaul inbound 8443 не изменён.
- В UFW удалено только правило с комментарием temp direct Reality; SSH, 8443, 51820, mtg backend и relay-specific rules сохранены.
- После cleanup новый VDSina VPN и Telegram paths повторно работают; публичный DE:443 больше не слушает.

## Evidence

- none
