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

Клиентские приложения и стратегия split routing: Hiddify-Next на Android, Karing + TUN на Windows, blacklist-подход через remote `.srs` rule-set'ы runetfreedom. Telegram Desktop не используется как индикатор корректности TUN и при отдельном MTProto выводится из VPN в `direct`.

## Guidance

- Android: **Hiddify-Next** (GitHub hiddify/hiddify-next). Импорт профиля через clipboard (vless://-ссылка с подменённым IP). Работает в VpnService режиме (tun2socks внутри клиента). **Уязвим к CVE локального SOCKS5** (habr.com/1020080), но альтернатив нет — все мобильные VLESS-клиенты страдают. Митигация на сервере через `geoip:ru blackhole`.
- Windows: **Karing** (GitHub KaringX/karing) с `TUN` mode на базе `sing-box`. Профиль импортируется через clipboard или profile file. Для Windows `TUN` требует запуск Karing от администратора.
- На Windows split routing строится через custom diversion groups и remote rule-set'ы `runetfreedom/russia-v2ray-rules-dat` в формате `.srs`, а не через локальный `geosite.dat`. Базовый маршрут: `ru-blocked -> proxy`, `private -> direct`, остальные локально доступные российские ресурсы не должны использовать VPN.
- Основные remote rule-set'ы для Karing:
- `https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-geosite/geosite-ru-blocked.srs`
- `https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-geoip/geoip-ru-blocked-community.srs`
- Если требуется принудительно вывести Telegram Desktop из VPN, используется отдельная custom diversion group `telegram-direct` с действием `Direct` и правилом `Process name = Telegram.exe`. Если матч по имени нестабилен, вместо него используется точный `Process path`. В Karing PC-процесс-матчинг чувствителен к регистру.
- Telegram Desktop не используется как verification target для `TUN`, если у пользователя отдельный MTProto-транспорт. Проверка TUN должна идти на приложении без собственного proxy-стека: например `Steam`, `Spotify`, `Epic Games Launcher` или другом обычном desktop-клиенте.
- Android Hiddify-Next сейчас **без split routing** — весь трафик идёт через туннель. В паре с серверным `geoip:ru → blackhole` это означает: ру-сайты не работают при включённом VPN на телефоне. Требуется отключать Hiddify для доступа к ру-сервисам. Backlog-задача — настроить routing rules в самом Hiddify (см. work-item).
- Формат share-ссылки для нового устройства (шаблон, UUID подставить свой): `vless://<UUID>@147.45.196.137:443?type=tcp&encryption=none&security=reality&pbk=9hE2DLpR6caqCS8FRZ9N4n2fsPTXcDuhVsuvXoGyAw8&fp=chrome&sni=www.microsoft.com&sid=444a941e4b8f&spx=%2F&flow=xtls-rprx-vision#reality-main-<device>`

## References

- decision:vpn-reality:clients:windows-system-proxy-over-tun
- decision:vpn-reality:clients:blacklist-over-whitelist-routing
- runbook:vpn-reality:clients:add-client
- https://habr.com/ru/articles/1020080/
- https://github.com/runetfreedom/russia-v2ray-rules-dat
- https://github.com/KaringX/karing
- https://karing.app/en/tutorial/diversion/
- https://karing.app/en/app-manual/diversion-rule-edit/
- https://github.com/hiddify/hiddify-next
