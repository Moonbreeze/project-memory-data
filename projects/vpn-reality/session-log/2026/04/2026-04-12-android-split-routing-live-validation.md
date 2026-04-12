---
date: 2026-04-12
recorded_at: 2026-04-12T15:47:24.258Z
project: vpn-reality
topic: android-split-routing-live-validation
source: user
status: active
---
# Session Note

## Summary

Живая проверка Android split routing на реальном устройстве пройдена: Karing с relay-first профилем работает, локально доступные российские сервисы идут корректно, домен из ru-blocked открывается через VPN.

## Actions

- На Android установлен и настроен Karing с relay-first профилем проекта.
- Включены `TUN`, корректный `Country Or Region`, `Private network direct connection` и custom group `ru-blocked` с remote runetfreedom .srs rule-set'ами.
- Пользователь подтвердил, что `ya.ru` работает корректно при включённом VPN.
- Пользователь подтвердил, что домен из `ru-blocked` открывается через VPN-маршрут.

## Follow-up

- Записать verification-result и привязать его к work-item `android-split-routing`.
- Закрыть work-item `android-split-routing` как done.
