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

Клиентские устройства получают relay-first профиль через Yandex relay. Для split routing и на Windows, и на Android проект теперь опирается на Karing + sing-box + TUN; Hiddify-Next остаётся только упрощённым fallback без кастомного split routing.

## Guidance

- Новый базовый профиль для устройств использует публичный endpoint Yandex relay `178.154.193.39:443`, а не прямой DE IP. Актуальный template share-ссылки: `vless://<UUID>@178.154.193.39:443?type=tcp&encryption=none&security=reality&pbk=zF486Nys3ZwxCtLW83cmwsXWvugaeP3cYk4rcYP9sgw&fp=chrome&sni=www.microsoft.com&sid=d155a5e6a588d95b&spx=%2F&flow=xtls-rprx-vision#ru-relay-<device>`.
- Android: если устройству нужен split routing, проект использует Karing + sing-box + TUN, а не Hiddify-Next. В Karing импортируется тот же relay-first профиль через clipboard/file, затем настраиваются diversion rules и remote .srs rule-set'ы runetfreedom.
- Android: Hiddify-Next допустим только как упрощённый клиент без custom split routing, если устройство не требует direct-исключений для российских сервисов.
- Windows: Karing + sing-box + TUN остаётся основным стеком. Для полного захвата CLI/desktop трафика Karing должен быть запущен `Run as administrator`, а `TUN Mode` должен быть реально поднят, не только включён в UI.
- Для split routing используется одна и та же логика Karing: private/local traffic остаётся direct, а custom diversion group `ru-blocked` с действием `Current Selected` использует remote rule-set'ы runetfreedom. На Windows возможны process-based direct exceptions; на Android доступны package-id based exceptions, если позже понадобится выводить отдельные приложения из VPN.
- Проверять клиентский выход нужно командами `curl -4 https://api4.ipify.org` и `curl https://api64.ipify.org`, где это возможно; ожидаемый результат — IPv4 `147.45.196.137` и IPv6 DE-exit. На Android, где CLI-проверка неудобна, минимумом считаются `ya.ru` с российским IP и домен из `ru-blocked`, который открывается через туннель.
- Если после миграции браузер показывает DE IP, а локально доступные российские сервисы ломаются, сначала проверять не сервер, а клиентский routing: корректен ли `Country Or Region`, активен ли `TUN`, скачались ли remote rule-set'ы и матчится ли `ru-blocked` в diversion detection.
- Старые share-ссылки на `147.45.196.137:443` считаются устаревшими для новых устройств. После полной миграции не раздавать прямой DE endpoint как основной профиль.

## References

- runbook:vpn-reality:add-device
- runbook:vpn-reality:yandex-relay-setup
- verification-result:vpn-reality:2026-04-12:stage3-yandex-cloud-relay
- verification-result:vpn-reality:2026-04-12:windows-karing-tun-routing
- decision:vpn-reality:2026-04-12:windows-karing-tun-over-system-proxy
- decision:vpn-reality:2026-04-12:android-karing-over-hiddify-for-split-routing
- decision:vpn-reality:2026-04-11:geoip-ru-blackhole
- https://github.com/KaringX/karing
- https://github.com/hiddify/hiddify-app
