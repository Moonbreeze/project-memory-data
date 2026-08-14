---
date: 2026-08-14
recorded_at: 2026-08-14T07:10:45.389Z
project: vpn-reality
topic: topology
registry_scope: infrastructure
source: agent
status: active
---
# Canonical Doc

## Summary

Текущая инфраструктура содержит два независимых relay-first контура через один Yandex entry и DE exit: VLESS Reality на relay:443 через Xray backhaul и Telegram MTProto на relay:9443 через отдельный WireGuard transport к закрытому mtg backend.

## Guidance

- RU-relay: Yandex Cloud VPS с публичным IPv4 178.154.193.39. Standalone Xray public inbound relay-public продолжает слушать 0.0.0.0:443 как VLESS + TCP + Reality + Vision; MTProto не делит с ним IP:443.
- Базовая REALITY-маскировка VPN-контура остаётся www.cloudflare.com. Новые VLESS client profiles используют relay:443 и только актуальные live pbk/sid из relay-public.
- DE-exit остаётся хостом 147.45.196.137 / 2a0f:cdc6:500:758::2. VPN backhaul inbound 8443/tcp использует VLESS + Reality + Vision, доступен только с публичного IP relay и не переиспользуется для MTProto.
- Постоянный Telegram proxy использует отдельный путь client -> 178.154.193.39:9443 -> HAProxy -> wg-mtg -> 10.66.0.2:3128 mtg -> Telegram. На relay HAProxy отправляет PROXY protocol v2, на DE mtg работает с proxy-protocol-listener = true.
- WireGuard адреса MTProto-контура: relay 10.66.0.1/30, DE 10.66.0.2/30. DE слушает 51820/udp; relay инициирует соединение к 147.45.196.137:51820 с PersistentKeepalive 25.
- Firewall boundary MTProto: DE разрешает WireGuard UDP только от 178.154.193.39, а mtg backend 10.66.0.2:3128 — только от 10.66.0.1 через wg-mtg. Публичный DE listener для mtg запрещён.
- Подтверждённая версия mtg — 2.2.8. Он слушает только 10.66.0.2:3128. Текущий FakeTLS fronting hostname — cloud.yandex.ru; изменение hostname создаёт новый secret и требует перевыдачи всех клиентских ссылок.
- MTProto secret и WireGuard private keys являются секретами: их нельзя включать в project-memory, runbooks, session notes или общие сообщения. Клиентская ссылка строится с публичными relay IP 178.154.193.39 и port 9443, а не с backend адресом из mtg access.
- Operational truth VPN остаётся relay-first client -> Yandex:443 -> DE:8443 -> internet. Проверка VPN использует api4.ipify.org/api64.ipify.org; диагностика MTProto отдельно использует HAProxy backend state, WireGuard handshake/transfer и Telegram client connection.
- Краткий начальный статус Telegram proxy Недоступен сразу после запуска допустим только как transient symptom. Если backend HAProxy UP и WG handshake свежий, повторить подключение; устойчивую недоступность расследовать по runbook two-hop-mtg-proxy.

## References

- runbook:vpn-reality:two-hop-mtg-proxy
- runbook:vpn-reality:yandex-relay-setup
- provider-note:vpn-reality:yandex-cloud
- verification-result:vpn-reality:2026-08-14:two-hop-mtg-proxy
- decision:vpn-reality:2026-08-14:two-hop-mtg-over-dedicated-wireguard
- verification-result:vpn-reality:2026-06-25:relay-public-cloudflare-mask-recovery
