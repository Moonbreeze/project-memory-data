---
date: 2026-04-11
recorded_at: 2026-04-11T16:25:07.370Z
project: vpn-reality
topic: aeza
source: agent
status: active
---
# Provider Note

## Overview

Aeza — хостер DE-exit VPS (147.45.196.137, Ubuntu, заявленный ДЦ — Германия). Используется как финальный exit-узел VLESS Reality.

## Constraints

- IPv6 присутствует (2a0f:cdc6:500:758::2), ifconfig.me по умолчанию отдаёт IPv6 — при проверках форсить -4.
- Порт 80 для Let's Encrypt HTTP-01 недоступен/проблемный — LE по IP не сработал.
- ASN принадлежит Aeza — публично известен как хостер-провайдер, что ухудшает anti-VPN скоринг у ряда сайтов.
- Доступ по SSH — только по ключу; исходно есть учётка moonbreeze с ключами с HUMGATE и moonbreeze-o.

## Guidance

- Перед публичными проверками использовать `curl -4 ifconfig.me`, иначе получите IPv6 и ложное впечатление о маршруте.
- Для TLS на панели использовать либо DNS-01 challenge, либо отдельный reverse proxy — HTTP-01 через 80-й порт не идёт.
- Если нужен чистый exit IP — цеплять Cloudflare WARP outbound (см. work-item cloudflare-warp-outbound-chain).
- ufw держать строгим: 22/tcp (SSH) + 443/tcp (VLESS Reality). Панель — только через SSH-туннель до появления домена.
