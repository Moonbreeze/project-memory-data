---
date: 2026-04-11
recorded_at: 2026-04-11T16:16:53.283Z
project: vpn-reality
topic: geoip-ru-blackhole
source: agent
status: active
---
# Decision

## Context

Статья habr.com/ru/articles/1020080 описала CVE в мобильных VLESS-клиентах (Hiddify, v2rayNG, NekoBox, Happ и др.): локальный SOCKS5 без авторизации на loopback, любой apk может обойти split tunneling, обратиться напрямую и узнать выходной IP VPS. Это даёт корреляционный вектор для фингерпринтинга выходных IP и их массовой блокировки. Пофиксить всех клиентов нельзя (патчей нет, все затронуты), заменить тоже нельзя (альтернатив на Android не существует).

## Decision

На Xray сервера VPS добавлено routing-правило `geoip:ru → blackhole` в routing.rules перед правилами по умолчанию. Любой исходящий трафик с VPS в сторону российских IP-диапазонов будет отбрасываться независимо от inbound-клиента.

## Consequences

- Плюс: даже если кто-то проэксплуатирует клиентский SOCKS5 и попытается обратиться через наш VPS к ру-сервису — выходной IP VPS никогда не засветится в логах ру-инфраструктуры, корреляционный вектор закрыт.
- Плюс: правило также даёт побочную защиту от случайной утечки трафика внутри туннеля к ру-сервисам (например, когда на клиенте split routing не настроен или сломался).
- Минус: пока VPN включён, любые запросы к ру-IP блокируются. Пользователь должен либо отключать VPN для доступа к ру-сервисам, либо настроить клиентский split routing (Bypass RU), который отправит такой трафик напрямую мимо VPS.
- Минус: ру-сайты, хостящиеся на Cloudflare/зарубежных CDN (habr, pikabu, lenta), не ловятся этим правилом как ру-трафик — они будут обработаны по общим правилам proxy/direct. Для них нужен отдельный слой на клиенте (список доменов, geosite:ru-blocked от runetfreedom).

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: Правило отражено в canonical-doc security/security-model и topology.
