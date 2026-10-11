---
date: 2026-10-11
recorded_at: 2026-10-11T20:27:17.534Z
project: vpn-reality
topic: vdsina-ru-relay-server-checks
source: agent
status: active
---
# Verification Result

## Scope

Серверная часть нового VDSina RU relay 138.16.175.166: managed services, WireGuard transport, DE backhaul и приватный mtg backend.

## Steps

- На DE подтверждены два WireGuard peer с раздельными AllowedIPs 10.66.0.1/32 и 10.67.0.1/32 и route 10.67.0.1 dev wg-mtg.
- На DE подтверждены адресные UFW allow для нового relay к 8443/tcp и 51820/udp и для 10.67.0.1 к 10.66.0.2:3128 через wg-mtg; старые и temporary direct-DE rules сохранены.
- На relay выполнен bootstrap с локальным Xray archive и обязательной pinned SHA-256 проверкой.
- Read-only check подтвердил свежий WireGuard handshake age 24s.
- Read-only TCP probes подтвердили доступность 147.45.196.137:8443 и 10.66.0.2:3128.
- Read-only check подтвердил active managed services, public listeners и HAProxy backend UP.

## Result

Серверная проверка пройдена. Новый relay связан с DE и оба backend пути доступны. Остались обязательные внешние проверки: клиентский VLESS Reality/authentication/DE egress и Telegram connection/messages/media/reconnect.
