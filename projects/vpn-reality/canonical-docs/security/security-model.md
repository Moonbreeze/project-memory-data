---
date: 2026-04-11
recorded_at: 2026-04-11T16:16:15.267Z
project: vpn-reality
topic: security-model
registry_scope: security
source: agent
status: active
---
# Canonical Doc

## Summary

Модель угроз и применённые митигации: Reality для маскировки, SSH-туннель вместо TLS для панели, geoip:ru blackhole как защита от CVE клиентского SOCKS5.

## Guidance

- Модель угроз: (a) DPI на уровне российского провайдера и ТСПУ, (b) активный probing выходных IP для занесения в список блокируемых, (c) фингерпринтинг через CVE-уязвимости локального SOCKS5 в мобильных VLESS-клиентах (habr 1020080). Не в модели: целенаправленные атаки на личность, APT, рут-компрометация VPS.
- Транспорт: VLESS+Reality с SNI-маской `www.microsoft.com` и flow `xtls-rprx-vision`. Для active probing выглядит как прямое HTTPS-подключение к microsoft.com — при попытке валидации TLS fallback на `www.microsoft.com:443` даёт валидный MS-сертификат.
- Доступ к панели 3x-ui: только SSH local port forward с `127.0.0.1:29486` на локальную машину. Public port 29486 в ufw закрыт. Причина: выбран путь без домена → Let's Encrypt не выписать → панель на plain HTTP. HTTP наружу неприемлем, значит не наружу.
- Серверное правило `geoip:ru → blocked` в Xray routing. Цель — нейтрализовать вектор фингерпринтинга: если клиентский SOCKS5 скомпрометирован и кто-то пустит обратный трафик к ру-сервису через VPS — выходной IP в логах ру-сервиса не появится, корреляция невозможна.
- Клиентские CVE-митигации: Windows использует v2rayN с System Proxy (xray-core, не sing-box) и blacklist routing — канала `tun2socks → local SOCKS5` нет вообще. Android невозможно полностью защитить на уровне клиента (все мобильные VLESS-клиенты уязвимы), защита строится только на сервере.
- Сознательно не в скоупе: Cloudflare WARP как outbound-цепь (стратегическая митигация из статьи), релей через Yandex Cloud (Layer 2 из оригинальной статьи), настоящая TLS-защита панели через LE+домен. Все вынесены в backlog, не блокируют текущий сетап.
- Fail2ban в 3x-ui активен по дефолту (`x-ui banlog` для просмотра). SSH порт нестандартный (51218), что срезает шум scan-атак. Pubkey-only auth закрывает оставшиеся векторы brute-force.

## References

- decision:vpn-reality:security:geoip-ru-blackhole
- decision:vpn-reality:operations:ssh-tunnel-over-le
- https://habr.com/ru/articles/1020080/
- https://habr.com/ru/articles/1021160/
