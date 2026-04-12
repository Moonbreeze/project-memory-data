---
date: 2026-04-12
recorded_at: 2026-04-12T15:03:13.030Z
project: vpn-reality
topic: security-model
registry_scope: security
source: agent
status: active
---
# Canonical Doc

## Summary

Модель угроз включает relay-слой в Yandex Cloud как mitigation против наиболее очевидного первого хопа в зарубежный хостинг, но не считает мобильные VLESS/sing-box клиенты защищёнными от localhost-proxy/loopback атак на самом устройстве. Android-клиент следует считать потенциально компрометируемым по exit IP; архитектура должна ограничивать ущерб от этого факта, а не игнорировать его.

## Guidance

- Состав модели угроз не меняется: (a) DPI/ТСПУ на российском провайдере, (b) активный probing и anti-VPN скоринг по публичным IP, (c) утечка exit IP через локальный proxy surface мобильного клиента на самом устройстве, включая обход `VpnService`/per-app split и сканирование `localhost` из hostile app/private space.
- Публичный клиентский вход находится на RU-relay в Yandex Cloud (`178.154.193.39:443`) и маскируется через `VLESS + Reality` с `www.microsoft.com` / `chrome`. Это уменьшает самый очевидный сетевой сигнал: первый хоп пользователя больше не выглядит как прямое подключение к зарубежному хостеру.
- Relay-first архитектура считается mitigation, а не fix для клиентской localhost-proxy проблемы. Если hostile app на Android узнаёт exit IP через локальный proxy клиента, relay это не предотвращает; он только разделяет `entry` и `egress`, уменьшая ущерб от компрометации одного IP.
- Android per-app split tunneling, package-based routing, Private Space/Knox/Shelter и похожие изоляции не считаются достаточной защитой от hostile app на том же устройстве, если клиент держит локальный proxy/control surface на loopback. Эти механизмы полезны для UX и маршрутизации, но не являются security boundary против локального spyware.
- DE VPS больше не принимает пользовательский трафик как primary public endpoint. На нём открыт отдельный backhaul inbound `8443/tcp`, доступный только с IPv4 relay `178.154.193.39`. Это сужает поверхность атаки: внешний наблюдатель или вредоносное приложение, узнавшее exit IP, не получает автоматически тот же endpoint, к которому подключается клиент.
- Серверное правило `geoip:ru -> blocked` на DE-exit остаётся обязательным. Отдельно клиент должен по возможности держать российские локально доступные сервисы в `direct`, чтобы российские приложения и сервисы не подтверждали использование VPN через корреляцию с DE egress.
- Следующий слой mitigation для утечки exit IP — отдельный egress fingerprint. Если anti-VPN скоринг по Aeza/hoster IP становится заметной проблемой, допустимый follow-up путь — вынести egress в Cloudflare WARP или другой отдельный outbound chain, не смешивая это с задачей hiding first hop.
- Проверка маршрута и operational validation по-прежнему опираются на `api4.ipify.org` и `api64.ipify.org`; `ifconfig.me` не использовать как единственный oracle. При анализе инцидентов различать: что атакующий мог узнать про `entry`, что про `egress`, и какой именно IP оказался скомпрометирован.

## References

- runbook:vpn-reality:yandex-relay-setup
- verification-result:vpn-reality:2026-04-12:stage3-yandex-cloud-relay
- decision:vpn-reality:2026-04-11:geoip-ru-blackhole
- decision:vpn-reality:2026-04-11:ssh-tunnel-over-le
- decision:vpn-reality:2026-04-12:android-karing-over-hiddify-for-split-routing
- https://habr.com/ru/articles/1020080/
- https://github.com/runetfreedom/per-app-split-bypass-poc
- https://github.com/cherepavel/VPN-Detector
- https://karing.app/en/faq/
- https://karing.app/en/tutorial/lan/
- https://karing.app/en/tutorial/online-panel/
