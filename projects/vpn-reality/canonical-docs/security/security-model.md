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

Модель угроз и применённые митигации теперь включают активный relay-слой в Yandex Cloud: клиентский первый хоп остаётся российским, а финальный выход идёт через DE-exit. Базовые митигации Reality, SSH-only panel access и geoip:ru blackhole на exit сохраняются.

## Guidance

- Модель угроз не меняется по составу: (a) DPI/ТСПУ на российском провайдере, (b) активный probing выходных IP, (c) фингерпринтинг через уязвимости локального SOCKS5 в мобильных VLESS-клиентах. Новый relay-слой уменьшает заметность прямого первого хопа в зарубежный хостинг, но не отменяет остальные митигации.
- Публичный клиентский вход теперь находится на RU-relay в Yandex Cloud (`178.154.193.39:443`) и маскируется через `VLESS + Reality` с `www.microsoft.com` / `chrome`, как и раньше. Для клиента первый сетевой контакт остаётся с российским IP, а не с немецким хостером.
- DE VPS больше не принимает пользовательский трафик как primary public endpoint. На нём открыт отдельный backhaul inbound `8443/tcp`, доступный только с IPv4 relay `178.154.193.39`. Это сужает поверхность атаки: probing 8443 из интернета не должен доходить до Xray.
- Серверное правило `geoip:ru -> blocked` на DE-exit остаётся обязательным. Relay не заменяет эту защиту: если клиентский SOCKS5-компонент скомпрометирован, корреляционный трафик к ру-сервисам всё равно не должен выходить с DE IP.
- Панель 3x-ui на DE по-прежнему доступна только через SSH local port forward. Relay-миграция не создаёт нового публичного admin endpoint и не требует открытия 29486/tcp.
- На Yandex relay порт `443/tcp` должен быть выделен только под Xray Reality inbound. Совмещение с MTProto или другим сервисом на том же `IP:443` не поддерживается в рабочем профиле проекта; сервис нужно переносить на другой порт/IP до ввода relay в прод.
- Проверка маршрута должна опираться на `api4.ipify.org` и `api64.ipify.org`; `ifconfig.me` может возвращать IPv6 observed address даже при IPv4-запросе и не подходит как надёжный security/operations oracle.

## References

- runbook:vpn-reality:yandex-relay-setup
- provider-note:vpn-reality:yandex-cloud
- verification-result:vpn-reality:2026-04-12:stage3-yandex-cloud-relay
- decision:vpn-reality:security:geoip-ru-blackhole
- decision:vpn-reality:operations:ssh-tunnel-over-le
- https://habr.com/ru/articles/1020080/
- https://habr.com/ru/articles/1021160/
