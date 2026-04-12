---
date: 2026-04-12
recorded_at: 2026-04-12T15:03:29.016Z
project: vpn-reality
topic: clients
registry_scope: client-setup
source: agent
status: active
---
# Canonical Doc

## Summary

Клиентские устройства теперь получают relay-first профиль: подключение к Yandex Cloud IP по VLESS Reality, а реальный exit остаётся немецким. На Windows остаётся Karing + TUN + split routing; проверять выход нужно по raw IPv4/IPv6 echo endpoints.

## Guidance

- Новый базовый профиль для устройств использует публичный endpoint Yandex relay `178.154.193.39:443`, а не прямой DE IP. Актуальный template share-ссылки: `vless://<UUID>@178.154.193.39:443?type=tcp&encryption=none&security=reality&pbk=zF486Nys3ZwxCtLW83cmwsXWvugaeP3cYk4rcYP9sgw&fp=chrome&sni=www.microsoft.com&sid=d155a5e6a588d95b&spx=%2F&flow=xtls-rprx-vision#ru-relay-<device>`.
- Android: Hiddify-Next остаётся рекомендуемым клиентом. Импорт через clipboard/file. Split routing на Android по-прежнему backlog; relay меняет только endpoint и не меняет клиентские ограничения Hiddify.
- Windows: Karing + sing-box + TUN остаётся основным стеком. Для полного захвата CLI/desktop трафика Karing должен быть запущен `Run as administrator`, а `TUN Mode` должен быть реально поднят, не только включён в UI.
- Проверять клиентский выход нужно командами `curl -4 https://api4.ipify.org` и `curl https://api64.ipify.org`. Ожидаемый результат — IPv4 `147.45.196.137` и IPv6 DE-exit. Проверка через `ifconfig.me` как единственный тест ненадёжна из-за смешения observed IPv4/IPv6.
- Если после миграции браузер показывает DE IP, а `curl` — домашний IP, сначала проверять не сервер, а клиентский режим: активен ли `TUN`, запущен ли Karing от администратора, не сидит ли приложение только на system proxy.
- Старые share-ссылки на `147.45.196.137:443` считаются устаревшими для новых устройств. После полной миграции не раздавать прямой DE endpoint как основной профиль.

## References

- runbook:vpn-reality:add-device
- runbook:vpn-reality:yandex-relay-setup
- verification-result:vpn-reality:2026-04-12:stage3-yandex-cloud-relay
- decision:vpn-reality:clients:windows-karing-tun-over-system-proxy
- decision:vpn-reality:security:geoip-ru-blackhole
- https://github.com/KaringX/karing
- https://github.com/hiddify/hiddify-next
