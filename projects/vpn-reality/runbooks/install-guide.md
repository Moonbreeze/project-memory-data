---
date: 2026-07-24
recorded_at: 2026-07-24T18:19:24.844Z
project: vpn-reality
topic: install-guide
source: agent
status: active
---
# Runbook

## Purpose

Короткая инструкция для нового пользователя в формате сообщения: скачать Karing, импортировать актуальную relay-first VLESS Reality ссылку, настроить Diversion и проверить, что VPN работает на Windows и Android.

## Procedure

- Скачать и установить актуальный `Karing` из официального релиза: `https://github.com/KaringX/karing/releases`.
- Открыть Karing.
- При первом запуске, если приложение спросит страну и добавит готовые правила, оставить `Country Or Region = Russia`, удалить всё, что Karing добавил по умолчанию кроме страны, и прокликать последующие экраны до `Done`.
- Получить актуальную share-ссылку у оператора контура и импортировать именно её. Для текущего проекта валидной считается relay-first ссылка на `178.154.193.39:443` с `security=reality` и `sni=www.cloudflare.com`; старые microsoft-based ссылки (`sni=www.microsoft.com`) считаются broken legacy и подлежат замене.
- В Karing открыть `Add Profiles` и выбрать `Import from Clipboard` или `Import Profile File`. В поле `Remark` указать любое удобное название подключения.
- Вернуться на главную страницу. Импортированный профиль будет выбран автоматически. Для подключения использовать большую кнопку внизу. На переключатель `System Proxy` не ориентироваться.
- Windows: полностью закрыть Karing и открыть заново через `Run as administrator`. Без этого VPN может работать неполноценно.
- Android: при первом включении подтвердить системный запрос на создание VPN-подключения.
- Huawei/EMUI: если VPN на этом устройстве потом начинает периодически мигать или переподключаться, для `Karing` сразу снять battery optimization, включить manual app launch / autostart и по возможности системный `Always-on VPN`.
- На главном экране открыть `Diversion`. Проверить `Country Or Region = Russia`. Затем открыть `Diversion Rules` и убедиться, что `Private network direct connection` включён, `Custom Diversion Group` включён, а рядом с ним до `GeoSite` больше нет лишних строк от дефолтной настройки.
- Открыть `Edit` (иконка карандаша) -> `Custom diversion group`. Создать новую группу и в поле `Remark` указать `ru-blocked`.
- Внутри группы `ru-blocked` добавить 2 отдельных правила типа `Rule Set`: `https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-geosite/geosite-ru-blocked.srs` и `https://raw.githubusercontent.com/runetfreedom/russia-v2ray-rules-dat/release/sing-box/rule-set-geoip/geoip-ru-blocked-community.srs`.
- Сохранить изменения и вернуться назад.
- В списке `Diversion rules` найти группу `ru-blocked` и выбрать для неё действие `Current Selected`.
- Выключить и снова включить VPN в Karing.
- Проверить подключение: открыть `https://api4.ipify.org` и убедиться, что показан IPv4 `147.45.196.137`. Затем открыть `https://ya.ru`. Если оба шага проходят, подключение настроено корректно.

## Verification

- Есть одна короткая инструкция в формате сообщения для Windows и Android.
- Инструкция требует импортировать актуальную relay-first ссылку, а не hardcoded legacy-профиль из старого сообщения.
- Текст явно фиксирует `sni=www.cloudflare.com` и помечает `www.microsoft.com` как broken legacy.
- Текст включает Huawei/EMUI troubleshooting note про battery optimization, manual app launch и `Always-on VPN` для Karing.
- Инструкция покрывает установку клиента, импорт профиля, настройку Diversion, добавление двух rule-set ссылок и проверку через `api4.ipify.org` и `ya.ru`.
- Текст соответствует текущему стеку проекта: `Karing + TUN + relay-first profile` с группой `ru-blocked`.
