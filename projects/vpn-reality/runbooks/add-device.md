---
date: 2026-07-24
recorded_at: 2026-07-24T20:24:17.037Z
project: vpn-reality
topic: add-device
source: agent
status: active
---
# Runbook

## Purpose

Развернуть VPN-клиент на новом устройстве (Android/Windows) через `Karing + TUN` с relay-first профилем и split routing. На Windows Telegram Desktop при отдельном MTProto исключается из VPN и идёт `direct`.

## Procedure

- Получить share-ссылку по runbook `add-client`.
- Android/Windows: установить актуальный `Karing` из https://github.com/KaringX/karing/releases.
- Windows: запускать `Karing` через `Run as administrator`, иначе `TUN` не поднимется.
- Android/Windows: `Add Profiles` → импортировать профиль через `Import from Clipboard` или `Import Profile File`. Выбрать импортированный профиль как активный.
- Android: при первом подключении подтвердить системное VPN-разрешение для `Karing`.
- Huawei/EMUI: если устройство Huawei, сразу проверить, что для `Karing` снята battery optimization, включены manual app launch / autostart и при необходимости системный `Always-on VPN`; при периодическом мигании кнопки подключения сначала лечить это как power management issue, а не как серверный сбой.
- Android/Windows: `Settings -> Diversion` → выставить `Country Or Region` по фактической стране пользователя. Для текущего сценария проекта это `Russia`, чтобы Karing добавил региональные geosite/geoip diversion rules.
- Android/Windows: в `Diversion rules` оставить включённым `Private network direct connection`.
- Android/Windows: `Settings -> Diversion -> Diversion rules -> Edit -> Custom diversion group` → создать группу `ru-blocked`. Внутрь добавить два правила типа `Rule Set`: `https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-geosite/geosite-ru-blocked.srs` и `https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-geoip/geoip-ru-blocked-community.srs`.
- Android/Windows: вернуться в `Diversion rules` и для группы `ru-blocked` выставить действие `Current Selected`, затем переподключить VPN.
- Android: базовая проверка — `ya.ru` открывается и показывает российский IP, а домен из `ru-blocked` открывается только через VPN-маршрут.
- Windows: если Telegram Desktop использует отдельный MTProto и не должен идти через VPN, создать группу `telegram-direct` и задать ей действие `Direct`. Внутрь добавить правило `Process name = Telegram.exe`. Если это не матчится, заменить на точный `Process path` к `Telegram.exe`. Оба типа правил в Karing чувствительны к регистру.
- Windows: проверка маршрутизации идёт не по Telegram, а по обычному non-browser приложению без собственного proxy-стека. Подходит `Steam`, `Spotify`, `Epic Games Launcher` или другой аналогичный клиент.
- Проверка: `ya.ru` открывается напрямую с российским IP; заблокированный в РФ домен идёт через VPN; выбранное non-browser приложение создаёт трафик в Karing при включённом `TUN`; Telegram Desktop остаётся работоспособным через свой MTProto и не является частью VPN-контура.

## Verification

- Android/Windows: профиль импортирован в `Karing`, `Country Or Region` выставлен по фактической стране, `ru-blocked` группа активна.
- Huawei/EMUI: для `Karing` снята battery optimization, включены manual app launch / autostart, если устройство проявляло фоновые отвалы.
- Windows: Karing запущен от администратора, `TUN` активен.
- `ya.ru` и другие российские домены открываются с российским IP клиента.
- Хотя бы один заблокированный в РФ домен из `ru-blocked` открывается через туннель.
- Хотя бы одно non-browser приложение без собственного proxy-стека создаёт трафик через `TUN`.
- Telegram Desktop исключён из VPN через `telegram-direct` и использует отдельный MTProto-контур, если такой контур включён у пользователя.
