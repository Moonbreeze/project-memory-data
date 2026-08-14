---
date: 2026-08-14
recorded_at: 2026-08-14T07:10:45.437Z
project: vpn-reality
topic: yandex-cloud
source: agent
status: active
---
# Provider Note

## Overview

Yandex Cloud используется как RU public-entry для двух независимых контуров: VLESS Reality на 178.154.193.39:443 через Xray backhaul и Telegram MTProto на 178.154.193.39:9443 через HAProxy и отдельный WireGuard transport к DE.

## Constraints

- Для Linux VM поддерживаемый operational path — SSH keys/metadata; password auth не использовать.
- 443/tcp выделен под Xray Reality inbound. MTProto использует отдельный 9443/tcp; shared IP:443 для MTProto и Reality не поддерживается.
- Yandex relay использует IPv4 как source к DE firewall rules. Включение IPv6 backhaul требует отдельного пересмотра firewall boundary.
- Для Xray bind на 443 системному пользователю требуется cap_net_bind_service; это не относится к HAProxy frontend 9443.
- Публичный 9443/tcp должен быть разрешён в Yandex security group/firewall, если внешний фильтр включён. Локальный UFW на relay на момент настройки был inactive.
- MTProto WireGuard peer на relay инициирует соединение к DE 147.45.196.137:51820; входной WireGuard UDP port на relay для этой схемы не требуется.
- MTProto secret и WireGuard private keys нельзя сохранять в provider note или project-memory.

## Guidance

- Сохранять Yandex relay как public-entry, а DE VPS как backhaul/exit; Xray и MTProto обслуживать как независимые контуры.
- На relay Xray остаётся на 443, HAProxy MTProto frontend — на 9443, backend — 10.66.0.2:3128 через wg-mtg.
- Для HAProxy backend обязательно send-proxy-v2, а на mtg — proxy-protocol-listener=true; иначе теряется исходный client IP или mtg отклоняет private source.
- После сетевых изменений VPN проверять через api4.ipify.org/api64.ipify.org, MTProto — через HAProxy backend UP, WG handshake и живое подключение Telegram.
- При изменении публичного relay IP перевыпускать и VLESS, и tg://proxy ссылки. При неизменном DE keypair backend secrets сами по себе не требуют ротации.
- Краткий стартовый статус Telegram proxy Недоступен может исчезнуть после установления backend/handshake; повторяющийся симптом расследовать, а не считать нормой.
