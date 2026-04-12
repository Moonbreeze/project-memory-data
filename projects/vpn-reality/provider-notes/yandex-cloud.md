---
date: 2026-04-12
recorded_at: 2026-04-12T15:05:26.078Z
project: vpn-reality
topic: yandex-cloud
source: agent
status: active
---
# Provider Note

## Overview

Yandex Cloud используется как RU-relay слой: публичный клиентский вход на `178.154.193.39:443`, standalone `xray` на Ubuntu, backhaul в DE-exit на `147.45.196.137:8443`.

## Constraints

- Для Linux VM нормальный operational path — SSH-ключи/metadata; попытки возвращаться к password auth не входят в supported workflow проекта.
- Порт `443/tcp` на relay должен быть выделен под `xray` Reality inbound. Если на VM уже живёт MTProto или другой сервис на `443`, его надо переносить до ввода relay в прод.
- Если `xray` запускается не от root/system user без capability, bind на `443/tcp` падает с `listen tcp 0.0.0.0:443: bind: permission denied`; лечится `setcap cap_net_bind_service=+ep` на бинарь Xray.
- Yandex relay в рабочем профиле проекта использует IPv4 как backhaul source к DE firewall rule. Если позже включать IPv6 backhaul, firewall boundary на DE надо пересмотреть отдельно, а не открывать `8443` всем по v6.
- На той же VM может крутиться дополнительный сервис вроде MTProto, но его портовая схема должна быть явно разведена с Xray; shared `IP:443` для MTProto и Reality не поддерживается.

## Guidance

- Хранить Yandex relay как отдельный слой роли `public entry`, а DE VPS — как `backhaul/exit`; не смешивать их operational responsibilities в одной памятке.
- После сетевых изменений проверять маршрут через `api4.ipify.org` и `api64.ipify.org`, а не через `ifconfig.me` главной страницей.
- Если клиент на Windows показывает разъезд между браузером и CLI, сначала проверять Karing `TUN`/admin mode, а не серверную сторону relay.
- При изменении публичного IP relay нужно перевыпускать share-ссылки клиентам, но DE public key/short-id при этом не меняются, если backhaul inbound не трогали.
