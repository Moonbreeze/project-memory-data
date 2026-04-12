---
date: 2026-04-11
recorded_at: 2026-04-11T16:18:58.330Z
project: vpn-reality
topic: windows-system-proxy-over-tun
source: agent
status: superseded
---
# Decision

## Context

v2rayN 7.x имеет два режима на Windows: TUN Mode (через встроенный sing-box) и System Proxy (через xray-core с HTTP/SOCKS прокси, который подцепляется как системный). Изначально включили TUN Mode ради прозрачного перехвата всего трафика. При попытке использовать категорию `geosite:ru-blocked` из runetfreedom geosite.dat Xray ядро стартовало успешно, но sing-box в TUN-режиме падал: он не читает `geosite.dat`, а пытается скачивать свой формат `.srs` из `2dust/sing-box-rules` на GitHub — а этих категорий там нет. Ошибка: `initial rule-set: geosite-ru-blocked: EOF`.

## Decision

На Windows используется **System Proxy** режим v2rayN (не TUN). Это переводит обработку правил на xray-core, который читает подменённый `geosite.dat` от runetfreedom корректно. TUN Mode возможен только после подключения sing-box-совместимых rule-set URL от runetfreedom (если они публикуются) или отказа от ru-blocked категорий в пользу инлайн-списка доменов.

## Consequences

- Плюс: runetfreedom geosite.dat работает, срабатывает `geosite:ru-blocked` и `geoip:ru-blocked-community`. Установленный System Proxy не требует TAP/WinTun драйверов и прав админа на каждом запуске.
- Минус: через System Proxy проходят только приложения, уважающие системные HTTP-proxy-настройки Windows: браузеры, Telegram Desktop, Discord частично. Steam, Spotify, игровые клиенты, большинство апов — нет. Для сценария обхода блокировок в браузере достаточно.
- Минус (принятый): если в будущем понадобится прокачать весь трафик машины (например, для игр или Steam), нужно будет либо вернуться к TUN Mode (с другим источником правил), либо искать альтернативы.
- Связка с CVE-митигацией: xray-core в режиме System Proxy не поднимает локальный SOCKS5 с `tun2socks`-обвязкой — значит, уязвимость из habr.com/1020080 на Windows не применима. Это положительный побочный эффект.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
