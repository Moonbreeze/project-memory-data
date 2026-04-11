---
date: 2026-04-11
recorded_at: 2026-04-11T16:20:11.605Z
project: vpn-reality
topic: blacklist-over-whitelist-routing
source: agent
status: active
---
# Decision

## Context

Изначально в v2rayN был выбран whitelist-пресет (`绕过大陆`, bypass mainland): всё через proxy, китайское/русское направо — напрямую. Попытка адаптировать его под Россию провалилась: стандартный v2fly `geosite.dat` не содержит категорий RU (ни `category-ru-ru`, ни `inside-ru`, ни `geolocation-ru`). Подмена на runetfreedom `geosite.dat` тоже не помогла: runetfreedom публикует списки **заблокированных в РФ** доменов (`ru-blocked`), не список «ру-сайтов для bypass». Плюс растёт доля ру-сервисов, хостящихся за рубежом (Habr, Pikabu, Lenta на Cloudflare) — `geoip:ru` их не ловит.

## Decision

Перешли на blacklist-подход: всё по умолчанию direct, через proxy пропускаются только явно перечисленные заблокированные домены/IP. Активный пресет: `V4-黑名单(Blacklist)` с добавленным правилом `RU blocked → proxy` (`geosite:ru-blocked`, `geoip:ru-blocked-community`). runetfreedom geosite.dat подменён в `bin/xray/` v2rayN.

## Consequences

- Плюс: любой ру-сайт (независимо от хостинга) работает напрямую. Cloudflare-хостинг с ру-аудиторией (Habr, Pikabu) больше не блокируется серверным `geoip:ru blackhole`, потому что клиент даже не отправляет этот трафик на VPS.
- Плюс: geosite:ru-blocked автоматически обновляется runetfreedom каждые 6 часов — не нужно вести ручной список заблокированных сайтов.
- Минус: если сайт заблокирован, но ещё не попал в список runetfreedom — он пойдёт direct и не откроется. Нужно либо ждать обновления, либо вручную добавлять в своё правило.
- Консистентность с серверным `geoip:ru blackhole`: сохраняется. Клиент больше не отправляет ру-трафик на VPS в принципе, серверное правило сработает только как fallback в случае эксплойта.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
