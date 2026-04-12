---
date: 2026-04-12
recorded_at: 2026-04-12T15:05:47.936Z
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
- Проверить, что в client params для relay используются актуальные значения: host `178.154.193.39`, `security=reality`, `sni=www.microsoft.com`, `pbk=zF486Nys3ZwxCtLW83cmwsXWvugaeP3cYk4rcYP9sgw`, `sid=d155a5e6a588d95b`, `fp=chrome`, `spx=%2F`, `flow=xtls-rprx-vision`, `type=tcp`, `encryption=none`.
- Перезапустить Xray на Yandex relay и убедиться, что конфиг валиден: `sudo xray run -test -config /usr/local/etc/xray/config.json`, затем `sudo systemctl restart xray`.
- Собрать share-ссылку вида `vless://<UUID>@178.154.193.39:443?type=tcp&encryption=none&security=reality&pbk=zF486Nys3ZwxCtLW83cmwsXWvugaeP3cYk4rcYP9sgw&fp=chrome&sni=www.microsoft.com&sid=d155a5e6a588d95b&spx=%2F&flow=xtls-rprx-vision#ru-relay-<device>`.
- Передать ссылку устройству защищённым каналом. Старые ссылки на прямой DE endpoint `147.45.196.137:443` не использовать для новых клиентов.
- После первого подключения проверить маршрут на устройстве: `curl -4 https://api4.ipify.org` должен показать `147.45.196.137`, `curl https://api64.ipify.org` — IPv6 DE-exit.

## Verification

- `/usr/local/etc/xray/config.json` на Yandex relay содержит новый UUID в `relay-public.settings.clients`.
- Импорт ссылки в клиент проходит без ошибок и профиль подключается к `178.154.193.39:443`.
- После подключения устройство выходит через DE-exit по raw echo endpoints.
