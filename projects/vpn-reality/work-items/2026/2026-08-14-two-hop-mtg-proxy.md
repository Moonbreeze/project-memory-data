---
date: 2026-08-14
recorded_at: 2026-08-14T07:09:23.341Z
project: vpn-reality
topic: two-hop-mtg-proxy
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Добавить постоянный двуххоповый MTProto proxy рядом с существующим relay-first VPN, не занимая Xray endpoint на 443/tcp.

## Outcome

Telegram подключается к Yandex relay на 9443/tcp, HAProxy передаёт соединения по отдельному WireGuard transport на закрытый mtg backend на DE, а существующий VLESS Reality контур остаётся без изменений.

## Provenance

- ad-hoc: Пользователь запросил постоянный Telegram MTProto proxy с переиспользованием существующих Yandex relay и DE exit ролей.

## Dependencies

- none

## Context

- none

## Verification

- WireGuard handshake между relay и DE активен, приватные адреса 10.66.0.1/10.66.0.2 доступны.
- HAProxy backend 10.66.0.2:3128 имеет состояние UP и публичный relay слушает 9443/tcp.
- mtg слушает только приватный WG-адрес, а Telegram-клиент подключается через relay endpoint.

## Evidence

- session-note:vpn-reality:2026-08-14:two-hop-mtg-proxy
- verification-result:vpn-reality:2026-08-14:two-hop-mtg-proxy
