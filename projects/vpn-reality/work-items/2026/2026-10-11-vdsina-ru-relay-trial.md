---
date: 2026-10-11
recorded_at: 2026-10-11T08:46:37.863Z
project: vpn-reality
topic: vdsina-ru-relay-trial
source: agent
status: archived
work_item_state: done
---
# Work Item

## Summary

Пробное развёртывание независимого RU relay в VDSina, Москва, с использованием существующего баланса пользователя.

## Outcome

Проверены VLESS Reality и MTProto пути через новый RU entry к существующему DE exit; temporary-direct-de остаётся резервом до отдельного cleanup решения.

## Provenance

- ad-hoc: Пользователь выбрал сначала попробовать VDSina, поскольку на аккаунте уже есть баланс. Создание платной VM выполняет пользователь в панели; агент готовит конфигурацию и диагностирует после предоставления адреса и SSH-доступа.

## Dependencies

- none

## Context

- none

## Verification

- VM VDSina в выбранной московской локации доступна по SSH, имеет публичный IPv4 и поддерживает WireGuard.
- Новый relay IP адресно разрешён на DE:8443/tcp и 51820/udp, приватный mtg backend не открыт публично.
- VPN через новый relay:443 получает DE egress по api4.ipify.org/api64.ipify.org; сайты и reconnect проверены пользователем.
- HAProxy relay:9443 имеет backend UP; WireGuard handshake свежий; Telegram connection, сообщения, media и reconnect работают.
- Новый WG peer не конфликтует с адресами и AllowedIPs старого Yandex relay; temporary direct-DE и старые правила не удалялись без отдельного решения.

## Evidence

- session-note:vpn-reality:2026-10-11:vdsina-ru-relay-bootstrap
- verification-result:vpn-reality:2026-10-11:vdsina-ru-relay-server-checks
- session-note:vpn-reality:2026-10-11:vdsina-ru-relay-client-validation
- verification-result:vpn-reality:2026-10-11:vdsina-ru-relay-end-to-end
