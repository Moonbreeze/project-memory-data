---
date: 2026-04-12
recorded_at: 2026-04-12T15:06:00.529Z
project: vpn-reality
topic: stage3-yandex-cloud-relay
source: agent
status: active
---
# Verification Result

## Scope

Relay-first path via Yandex Cloud entry and DE backhaul/exit

## Steps

- На DE firewall удалён общий `8443/tcp ALLOW Anywhere`; оставлено правило `8443/tcp ALLOW 178.154.193.39` для backhaul от relay.
- На Yandex VPS порт `443/tcp` освобождён под Xray Reality inbound; MTProto перенесён с `443` на другой порт.
- На Yandex relay Xray получил capability для bind на low port после ошибки `listen tcp 0.0.0.0:443: bind: permission denied` и успешно поднял inbound на `443/tcp`.
- На клиенте через Karing/TUN выполнены проверки `curl -4 https://api4.ipify.org` и `curl https://api64.ipify.org`.
- Проверка через `ifconfig.me` признана ненадёжной из-за смешения observed IPv4/IPv6 и не использовалась как финальный oracle.

## Result

Миграция подтверждена: публичный клиентский вход работает через Yandex relay `178.154.193.39:443`, а внешний IP клиента остаётся DE-exit — IPv4 `147.45.196.137` и IPv6 `2a0f:cdc6:500:758::2`. Firewall boundary на DE сузился до backhaul только с IP relay.
