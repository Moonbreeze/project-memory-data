---
date: 2026-04-12
recorded_at: 2026-04-12T15:47:24.361Z
project: vpn-reality
topic: android-karing-split-routing
source: user
status: active
---
# Verification Result

## Scope

Android client split routing with Karing + TUN + relay-first profile

## Steps

- На Android импортирован relay-first профиль `vless://...@178.154.193.39:443` в Karing и выдано системное VPN-разрешение.
- В Karing выставлен корректный `Country Or Region`, включён `Private network direct connection`, добавлена custom group `ru-blocked` с remote runetfreedom rule-set'ами.
- После reconnect проверен локально доступный российский сервис `ya.ru`.
- После reconnect проверен домен из `ru-blocked`.

## Result

Проверка пройдена. Android-клиент на Karing с TUN и relay-first профилем ведёт себя как ожидается: `ya.ru` работает корректно при включённом VPN, а домен из `ru-blocked` открывается через туннель. Это подтверждает, что миграция Android-сценария со схемы Hiddify-only на Karing + split routing технически состоялась.
