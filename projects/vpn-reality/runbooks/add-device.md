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

Развернуть VPN-клиент на новом устройстве (Android/Windows) с разделением трафика через blacklist-маршрутизацию. На Windows Telegram Desktop при отдельном MTProto исключается из VPN и идёт `direct`.

## Procedure

- Получить share-ссылку по runbook `add-client`.
- Android: установить Hiddify-Next из Google Play → Add profile from clipboard → Connect. Split routing пока не настроен, см. work-item `android-split-routing`.
- Windows: установить актуальный `Karing` из https://github.com/KaringX/karing/releases и запускать его `Run as administrator`, иначе `TUN` не поднимется.
- Windows: `Add Profiles` → импортировать профиль через `Import from Clipboard` или `Import Profile File`. Выбрать импортированный профиль как активный.
- Windows: `Settings -> Diversion -> Diversion rules -> Edit -> Custom diversion group` → создать группу `ru-blocked`. Внутрь добавить два правила типа `Rule Set`:
- `https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-geosite/geosite-ru-blocked.srs`
- `https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-geoip/geoip-ru-blocked-community.srs`
- Windows: вернуться в `Diversion rules` и для группы `ru-blocked` выставить действие `Current Selected`, затем переподключить VPN.
- Windows: если Telegram Desktop использует отдельный MTProto и не должен идти через VPN, создать группу `telegram-direct` и задать ей действие `Direct`. Внутрь добавить правило `Process name = Telegram.exe`. Если это не матчится, заменить на точный `Process path` к `Telegram.exe`. Оба типа правил в Karing чувствительны к регистру.
- Windows: проверка маршрутизации идёт не по Telegram, а по обычному non-browser приложению без собственного proxy-стека. Подходит `Steam`, `Spotify`, `Epic Games Launcher` или другой аналогичный клиент.
- Проверка: `ya.ru` открывается напрямую с российским IP; заблокированный в РФ домен идёт через VPN; выбранное non-browser приложение создаёт трафик в Karing при включённом `TUN`; Telegram Desktop остаётся работоспособным через свой MTProto и не является частью VPN-контура.

## Verification

- Windows: Karing запущен от администратора, `TUN` активен, импортированный профиль выбран текущим.
- `ya.ru` и другие российские домены открываются с российским IP клиента.
- Хотя бы один заблокированный в РФ домен из `ru-blocked` открывается через туннель.
- Хотя бы одно non-browser приложение без собственного proxy-стека создаёт трафик через `TUN`.
- Telegram Desktop исключён из VPN через `telegram-direct` и использует отдельный MTProto-контур, если такой контур включён у пользователя.
