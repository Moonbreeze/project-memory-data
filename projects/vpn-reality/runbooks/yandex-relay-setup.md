---
date: 2026-07-24
recorded_at: 2026-07-24T18:19:24.865Z
project: vpn-reality
topic: yandex-relay-setup
source: agent
status: active
---
# Runbook

## Purpose

Поднять и проверить relay-first схему `client -> Yandex Cloud relay -> DE exit` для VLESS Reality, не ломая security boundary на DE.

## Procedure

- Подготовить Yandex VPS: SSH-доступ по ключу, Ubuntu с `sudo`, публичный IPv4. Если на `443/tcp` уже висит MTProto или другой сервис, сначала перенести его на другой порт или IP.
- На Yandex relay установить `xray` и сгенерировать параметры: один публичный client UUID, отдельный backhaul UUID для линка relay -> DE, отдельные Reality keypair/short-id для публичного relay и отдельные Reality keypair/short-id для DE backhaul inbound.
- На DE открыть 3x-ui через SSH runbook `panel-access` и создать отдельный inbound `relay-backhaul` на `8443/tcp`: `VLESS`, `TCP`, `Reality`, `xtls-rprx-vision`, `dest/serverName = www.cloudflare.com:443`, `fingerprint = chrome`, с отдельным UUID для relay.
- На DE ограничить firewall: `8443/tcp` разрешить только с IP Yandex relay. Удалить общий `ALLOW Anywhere` для 8443 и не держать публичный IPv6 allow для 8443, если relay ходит только по IPv4.
- На Yandex relay создать `/usr/local/etc/xray/config.json` со схемой: inbound `relay-public` на `0.0.0.0:443` (`VLESS + Reality + Vision`) и outbound `de-backhaul` на `147.45.196.137:8443` (`VLESS + Reality + Vision`). Для обоих уровней relay-first схемы использовать cloudflare-based REALITY маскировку; relay outbound `de-backhaul.serverName` должен совпадать с `www.cloudflare.com`.
- Если Xray не может слушать `443/tcp` с ошибкой `bind: permission denied`, выдать capability бинарю: `sudo setcap 'cap_net_bind_service=+ep' $(command -v xray)` и перезапустить сервис.
- Проверить конфиг и сервис на Yandex: `sudo xray run -test -config /usr/local/etc/xray/config.json`, затем `sudo systemctl enable --now xray`, `sudo ss -ltnp | grep :443`.
- Собрать и раздать новую share-ссылку на Yandex IP с актуальными live `relay-public` параметрами. Старый прямой DE endpoint не использовать как primary path для новых устройств; старые microsoft-based share-ссылки считать legacy и перевыдавать.
- На клиенте проверить маршрут по raw echo endpoints: `curl -4 https://api4.ipify.org` должен вернуть `147.45.196.137`, а `curl https://api64.ipify.org` — IPv6 DE-exit. Не использовать `ifconfig.me` как единственный тест.
- Если одновременно ломаются несколько устройств без изменения локальных настроек, первым делом проверять REALITY handshake и совпадение mask host на relay public side и DE backhaul, а не клиентский routing.
- Если на Windows браузер уже идёт через VPN, а `curl` показывает домашний IP, проверить не сервер, а клиент: Karing должен быть запущен от администратора, `TUN Mode` реально поднят, режим `Rule/Global` соответствует ожидаемому routing policy.
- После успешной проверки выключить старый прямой inbound на DE, если fallback не нужен, и прибрать лишние firewall rules/резервные порты.

## Verification

- На клиенте `curl -4 https://api4.ipify.org` возвращает `147.45.196.137`.
- На клиенте `curl https://api64.ipify.org` возвращает IPv6 DE-exit.
- На Yandex relay `sudo ss -ltnp | grep :443` показывает слушающий `xray`.
- На DE firewall не содержит общего `8443/tcp ALLOW Anywhere`; backhaul доступен только с IP relay.
- Public relay inbound и DE backhaul используют согласованный cloudflare-based REALITY mask host.
