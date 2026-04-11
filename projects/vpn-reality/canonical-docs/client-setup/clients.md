---
date: 2026-04-11
recorded_at: 2026-04-11T16:12:24.457Z
project: vpn-reality
topic: clients
registry_scope: client-setup
source: agent
status: active
---
# Canonical Doc

## Summary

Клиентские приложения и стратегия split routing: Hiddify-Next на Android, v2rayN + System Proxy на Windows, blacklist-подход через runetfreedom geosite.dat.

## Guidance

- Android: **Hiddify-Next** (GitHub hiddify/hiddify-next). Импорт профиля через clipboard (vless://-ссылка с подменённым IP). Работает в VpnService режиме (tun2socks внутри клиента). **Уязвим к CVE локального SOCKS5** (habr.com/1020080), но альтернатив нет — все мобильные VLESS-клиенты страдают. Митигация на сервере через `geoip:ru blackhole`.
- Windows: **v2rayN 7.20.2** (github.com/2dust/v2rayN). Качать `v2rayN-windows-64-desktop.zip`, импорт через `Ctrl+V` (Import bulk URL from clipboard). В этом проекте сознательно используется **System Proxy**, а не TUN mode — обоснование в decision clients/windows-system-proxy-over-tun.
- На Windows в режиме System Proxy трафик проходит через **xray-core** (не sing-box). Это важно, потому что `geosite.dat` от runetfreedom читается только xray, а sing-box в TUN-режиме использует другой формат `.srs` и другие источники.
- `geosite.dat` от runetfreedom/russia-v2ray-rules-dat положен в папку `bin/xray/` v2rayN (перезаписью дефолта). Он публикует списки заблокированных в РФ доменов (category `ru-blocked`), не список ру-доменов для bypass. Это диктует **blacklist**-подход к routing.
- Активный routing preset v2rayN: `V4-黑名单(Blacklist)`. Логика: всё по умолчанию идёт `direct`, через `proxy` пропускаются только явно указанные категории и домены. Domain strategy: `IPIfNonMatch`.
- Ключевое добавленное правило: `RU blocked → proxy`, с `domain: geosite:ru-blocked` и `ip: geoip:ru-blocked-community`. Стандартные правила blacklist-пресета (google, facebook, netflix, GFW) оставлены.
- Android Hiddify-Next сейчас **без split routing** — весь трафик идёт через туннель. В паре с серверным `geoip:ru → blackhole` это означает: ру-сайты не работают при включённом VPN на телефоне. Требуется отключать Hiddify для доступа к ру-сервисам. Backlog-задача — настроить routing rules в самом Hiddify (см. work-item).
- Формат share-ссылки для нового устройства (шаблон, UUID подставить свой): `vless://<UUID>@147.45.196.137:443?type=tcp&encryption=none&security=reality&pbk=9hE2DLpR6caqCS8FRZ9N4n2fsPTXcDuhVsuvXoGyAw8&fp=chrome&sni=www.microsoft.com&sid=444a941e4b8f&spx=%2F&flow=xtls-rprx-vision#reality-main-<device>`

## References

- decision:vpn-reality:clients:windows-system-proxy-over-tun
- decision:vpn-reality:clients:blacklist-over-whitelist-routing
- runbook:vpn-reality:clients:add-client
- https://habr.com/ru/articles/1020080/
- https://github.com/runetfreedom/russia-v2ray-rules-dat
- https://github.com/2dust/v2rayN
- https://github.com/hiddify/hiddify-next
