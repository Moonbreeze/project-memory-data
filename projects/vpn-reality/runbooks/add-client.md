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

Добавить нового клиента (устройство) в существующий VLESS Reality inbound и получить готовую share-ссылку с уже подставленным публичным IP.

## Procedure

- Открыть панель по runbook `panel-access` (SSH local port forward на 127.0.0.1:29486).
- Inbounds → найти inbound `reality-main` (port 443, VLESS+Reality+Vision) → кнопка `+` в колонке Clients.
- Email/remark: `<device-slug>` (например `desktop-windows-2`). UUID — сгенерировать кнопкой. Flow обязательно `xtls-rprx-vision`. Subscription/TgId/IP limit — пусто. Expiry — 0.
- Сохранить. Из списка клиентов скопировать QR/URL — в ней уже должен быть `147.45.196.137:443`, потому что на inbound `reality-main` настроен External Proxy entry `Forced Expose IP = 147.45.196.137` (см. canonical-doc infrastructure/topology). Ручная замена хоста больше не требуется.
- Если в скопированной ссылке внезапно снова `127.0.0.1` или внутреннее доменное имя — проверить в Inbound Edit, что External Proxy entry не удалён и `Forced Expose IP = 147.45.196.137`. Восстановить при необходимости.
- Проверить глазами, что в `vless://` URL есть все Reality-параметры: `security=reality`, `sni=www.microsoft.com`, `pbk=9hE2DLpR6caqCS8FRZ9N4n2fsPTXcDuhVsuvXoGyAw8`, `sid=444a941e4b8f`, `fp=chrome`, `spx=%2F`, `flow=xtls-rprx-vision`, `type=tcp`, `encryption=none`. Отсутствие любого — стоп, не раздавать.
- Ремарк в ssh-fragment'е ссылки (после `#`) будет вида `reality-main-<device-slug>-public-ipv4` — суффикс `-public-ipv4` подклеивается из remark самого External Proxy entry, это косметика и на функционал не влияет.
- Передать ссылку на устройство защищённым каналом (не в открытых мессенджерах).

## Verification

- `/usr/local/x-ui/bin/config.json` содержит новый UUID в `inbounds[0].settings.clients`.
- Импорт ссылки в v2rayN/Hiddify проходит без ошибок, поле Flow подхватывается как `xtls-rprx-vision`, хост — `147.45.196.137` без ручных правок.
- После подключения `curl ifconfig.me` с клиента возвращает `147.45.196.137`.
