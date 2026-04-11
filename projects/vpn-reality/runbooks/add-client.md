---
date: 2026-04-11
recorded_at: 2026-04-11T16:23:14.005Z
project: vpn-reality
topic: add-client
source: agent
status: active
---
# Runbook

## Purpose

Добавить нового клиента (устройство) в существующий VLESS Reality inbound и получить готовую share-ссылку.

## Procedure

- Открыть панель по runbook `panel-access`.
- Inbounds → найти inbound `reality-main` (port 443, VLESS+Reality+Vision) → кнопка `+` в колонке Clients.
- Email/remark: `<device-slug>` (например `desktop-windows-2`). UUID — сгенерировать кнопкой. Flow обязательно `xtls-rprx-vision`. Subscription/TgId/IP limit — пусто. Expiry — 0.
- Сохранить. Из списка клиентов скопировать QR/URL.
- В полученной `vless://` ссылке заменить хост (127.0.0.1 или доменное имя из панели) на `147.45.196.137`. Параметры `sni=www.microsoft.com`, `pbk`, `sid`, `spx=%2F`, `fp=chrome`, `flow=xtls-rprx-vision` должны остаться.
- Передать ссылку на устройство защищённым каналом (не в открытых мессенджерах).

## Verification

- `/usr/local/x-ui/bin/config.json` содержит новый UUID в `inbounds[0].settings.clients`.
- Импорт ссылки в v2rayN/Hiddify проходит без ошибок и поле Flow подхватывается как `xtls-rprx-vision`.
- После подключения `curl ifconfig.me` с клиента возвращает `147.45.196.137`.
