---
date: 2026-08-14
recorded_at: 2026-08-14T07:09:43.591Z
project: vpn-reality
topic: two-hop-mtg-proxy
source: agent
status: active
---
# Session Note

## Summary

Развёрнут постоянный двуххоповый MTProto proxy поверх существующих ролей Yandex relay и DE exit без изменений рабочего Xray Reality контура.

## Actions

- На DE подтверждена Ubuntu 22.04 и сохранены существующие Xray/Docker сервисы без изменения их портов.
- На DE поднят отдельный WireGuard интерфейс wg-mtg с адресом 10.66.0.2/30 и listener 51820/udp; peer ограничен relay-адресом 10.66.0.1/32.
- На DE установлен закреплённый mtg v2.2.8 с проверкой release SHA-256; сервис слушает только 10.66.0.2:3128 и ожидает PROXY protocol.
- На DE firewall разрешает WireGuard transport только от публичного IP relay и backend 3128/tcp только от 10.66.0.1 через wg-mtg.
- На Yandex relay поднят wg-mtg 10.66.0.1/30 с endpoint DE 147.45.196.137:51820 и PersistentKeepalive 25.
- В существующий HAProxy на relay добавлен TCP frontend 0.0.0.0:9443 и backend 10.66.0.2:3128 с send-proxy-v2; Xray продолжает занимать 443/tcp.
- Для mtg создан FakeTLS secret с fronting hostname cloud.yandex.ru; сам secret и private keys в project-memory не сохранены.
- После устранения недостающего DE UFW allow HAProxy backend перешёл в UP; Telegram сначала кратковременно показывал proxy как недоступный, затем успешно подключился.

## Follow-up

- При ротации секрета выдавать новую tg://proxy ссылку защищённым каналом и не сохранять secret в project-memory.
- При недоступности сначала проверять HAProxy backend state, затем WireGuard handshake и DE UFW rule для 10.66.0.1 -> 10.66.0.2:3128.
- При возможности провести отдельную продолжительную проверку загрузки крупных медиа и reconnect после перезапуска обоих VPS.
