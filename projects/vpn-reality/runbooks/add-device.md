---
date: 2026-04-11
recorded_at: 2026-04-11T16:23:38.839Z
project: vpn-reality
topic: add-device
source: agent
status: active
---
# Runbook

## Purpose

Развернуть VPN-клиент на новом устройстве (Android/Windows) с разделением трафика через blacklist-маршрутизацию.

## Procedure

- Получить share-ссылку по runbook `add-client`.
- Android: установить Hiddify-Next из Google Play → Add profile from clipboard → Connect. Split routing пока не настроен, см. work-item `android-split-routing`.
- Windows: установить v2rayN 7.20.2+ (https://github.com/2dust/v2rayN/releases) в отдельный каталог. Core — встроенный Xray.
- Windows: Servers → Import bulk URL from clipboard. Выбрать импортированный сервер, Set as active server.
- Windows: Routing Setting → выбрать preset `V4-黑名单 (Blacklist)` → ОК. Это направляет geoip:cn/ru/private + мультикаст в direct, остальное в proxy.
- Windows: подложить свежий runetfreedom geosite.dat. Скачать с https://github.com/runetfreedom/russia-v2ray-rules-dat → положить в `%APPDATA%\v2rayN\bin\xray\geosite.dat` (заменить). Теперь в blacklist правилах `geosite:ru-blocked` доступен.
- Windows: в Rule List правила blacklist → добавить `geosite:ru-blocked` → proxy (ru-blocked — это домены заблокированные в РФ, которые надо гнать через VPN).
- Windows: System Proxy → Set system proxy (НЕ TUN mode — см. decision `windows-system-proxy-over-tun`).
- Проверка: `curl ifconfig.me` (проксируется) → IP немецкий; открыть ya.ru → напрямую, IP клиента; открыть заблокированный в РФ сайт → работает через прокси.

## Verification

- Windows: в v2rayN статусбаре индикатор `System Proxy: On` и выбранный сервер reality-main.
- IP-чек через браузер на ifconfig.me показывает 147.45.196.137 только для сайтов вне ru/cn.
- `ya.ru` и другие российские домены открываются с российским IP клиента.
- Хотя бы один заблокированный в РФ домен из `ru-blocked` открывается через туннель.
