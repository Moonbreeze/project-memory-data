---
date: 2026-07-24
recorded_at: 2026-07-24T18:19:24.827Z
project: vpn-reality
topic: add-client-relay
source: agent
status: active
---
# Runbook

## Purpose

Добавить новое устройство в текущую relay-first схему и выдать ему корректную share-ссылку на Yandex relay, а не на прямой DE endpoint.

## Procedure

- Открыть Yandex relay конфиг `/usr/local/etc/xray/config.json` и найти inbound `relay-public` на `443/tcp`.
- Сгенерировать новый UUID для устройства (`xray uuid`) и добавить его в массив `settings.clients` inbound `relay-public` с `flow = xtls-rprx-vision` и понятным `email`/remark устройства.
- Перед выдачей профиля снять актуальные live параметры именно с `relay-public`: public key, short-id, `serverNames`/`sni`, fingerprint и порт. Не брать эти значения из старых заметок или исторических шаблонов.
- Считать cloudflare-based маскировку обязательной: для новых устройств использовать `sni=www.cloudflare.com`; старые microsoft-based ссылки (`sni=www.microsoft.com`) больше не выдавать.
- Перезапустить Xray на Yandex relay и убедиться, что конфиг валиден: `sudo xray run -test -config /usr/local/etc/xray/config.json`, затем `sudo systemctl restart xray`.
- Собрать share-ссылку вида `vless://<UUID>@178.154.193.39:443?...&security=reality&pbk=<relay-public-pbk>&fp=chrome&sni=www.cloudflare.com&sid=<relay-public-sid>&spx=%2F&flow=xtls-rprx-vision#ru-relay-<device>`.
- Передать ссылку устройству защищённым каналом. Старые ссылки на прямой DE endpoint `147.45.196.137:443` не использовать для новых клиентов.
- После первого подключения проверить маршрут на устройстве: `curl -4 https://api4.ipify.org` должен показать `147.45.196.137`, `curl https://api64.ipify.org` — IPv6 DE-exit.

## Verification

- `/usr/local/etc/xray/config.json` на Yandex relay содержит новый UUID в `relay-public.settings.clients`.
- Выданная клиенту ссылка использует `178.154.193.39:443`, `sni=www.cloudflare.com` и актуальные live `relay-public` параметры.
- Импорт ссылки в клиент проходит без ошибок и профиль подключается к `178.154.193.39:443`.
- После подключения устройство выходит через DE-exit по raw echo endpoints.
