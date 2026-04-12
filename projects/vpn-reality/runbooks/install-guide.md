---
date: 2026-04-12
recorded_at: 2026-04-12T16:55:27.020Z
project: vpn-reality
topic: install-guide
source: agent
status: active
---
# Runbook

## Purpose

Короткая инструкция для нового пользователя в формате сообщения: скачать Karing, импортировать relay-first VLESS Reality ссылку, настроить Diversion и проверить, что VPN работает на Windows и Android.

## Procedure

- Скачать и установить Karing. Android: `https://github.com/KaringX/karing/releases/download/v1.2.17.2000/karing_1.2.17.2000_android_arm.apk`. Windows: `https://github.com/KaringX/karing/releases/download/v1.2.17.2000/karing_1.2.17.2000_windows_x64.exe`. Альтернативно открыть `https://github.com/KaringX/karing/releases` и раскрыть `Assets` у самого верхнего релиза.
- Открыть Karing.
- При первом запуске, если приложение спросит страну и добавит готовые правила, оставить `Country Or Region = Russia`, удалить всё, что Karing добавил по умолчанию кроме страны, и прокликать последующие экраны до `Done`.
- Скопировать и импортировать ссылку: `vless://d45aa9ee-8a6f-4a73-a0c6-9e4b4eb8ede3@178.154.193.39:443?type=tcp&encryption=none&security=reality&pbk=zF486Nys3ZwxCtLW83cmwsXWvugaeP3cYk4rcYP9sgw&fp=chrome&sni=www.microsoft.com&sid=d155a5e6a588d95b&spx=%2F&flow=xtls-rprx-vision#ru-relay`. В Karing открыть `Add Profiles` и выбрать `Import from Clipboard`. В поле `Remark` указать любое удобное название подключения.
- Вернуться на главную страницу. Импортированный профиль будет выбран автоматически. Для подключения использовать большую кнопку внизу. На переключатель `System Proxy` не ориентироваться.
- Windows: полностью закрыть Karing и открыть заново через `Run as administrator`. Без этого VPN может работать неполноценно.
- Android: при первом включении подтвердить системный запрос на создание VPN-подключения.
- На главном экране открыть `Diversion`. Проверить `Country Or Region = Russia`. Затем открыть `Diversion Rules` и убедиться, что `Private network direct connection` включён, `Custom Diversion Group` включён, а рядом с ним до `GeoSite` больше нет лишних строк от дефолтной настройки.
- Открыть `Edit` (иконка карандаша) -> `Custom diversion group`. Создать новую группу и в поле `Remark` указать `ru-blocked`.
- Внутри группы `ru-blocked` добавить 2 отдельных правила типа `Rule Set`: `https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-geosite/geosite-ru-blocked.srs` и `https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-geoip/geoip-ru-blocked-community.srs`.
- Сохранить изменения и вернуться назад.
- В списке `Diversion rules` найти группу `ru-blocked` и выбрать для неё действие `Current Selected`.
- Выключить и снова включить VPN в Karing.
- Проверить подключение: открыть `https://api4.ipify.org` и убедиться, что показан IPv4 `147.45.196.137`. Затем открыть `https://ya.ru`. Если оба шага проходят, подключение настроено корректно.

## Verification

- Есть одна короткая инструкция в формате сообщения для Windows и Android.
- Инструкция покрывает установку клиента, импорт профиля из relay-first ссылки, настройку Diversion, добавление двух rule-set ссылок и проверку через `api4.ipify.org` и `ya.ru`.
- Текст соответствует текущему стеку проекта: `Karing + TUN + relay-first profile` с группой `ru-blocked`.
