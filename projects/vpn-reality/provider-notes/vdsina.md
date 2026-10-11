---
date: 2026-10-11
recorded_at: 2026-10-11T20:00:03.297Z
project: vpn-reality
topic: vdsina
source: agent
status: active
---
# Provider Note

## Overview

VDSina используется для пробного нового RU relay с публичным IPv4 138.16.175.166; локальный Windows SSH alias для этого узла — `ruhop`.

## Constraints

- SSH username, identity и нестандартный порт задаются локальным alias `ruhop`; в пользовательских Windows-командах не дублировать эти параметры.
- Целевые публичные listeners relay: 443/tcp для VLESS Reality и 9443/tcp для Telegram HAProxy.
- Relay должен обращаться к DE 147.45.196.137 по 8443/tcp и 51820/udp; WireGuard relay address выбран 10.67.0.1/32.
- Маршрут relay к GitHub release CDN оказался нестабильным; Xray доставляется проверенным локальным архивом с обязательной pinned SHA-256 проверкой.
- Private keys, UUID, Reality parameters и MTProto secret нельзя сохранять в provider note или project-memory.

## Guidance

- Для Windows-команд подключения, SCP и доставки использовать SSH alias `ruhop`. Для DE использовать alias `dev`.
- До отключения temporary direct-DE Reality проверить оба пути через новый relay и оставить старый Yandex peer/rules как резерв.
- Для Xray bootstrap использовать `--xray-archive secrets/tools/xray.zip`; не обходить checksum verification.
- На DE добавлять адресные allow rules только для 138.16.175.166 и отдельный WireGuard peer AllowedIPs 10.67.0.1/32, не заменяя существующий peer.
