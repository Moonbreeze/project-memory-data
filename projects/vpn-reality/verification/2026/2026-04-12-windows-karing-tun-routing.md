---
date: 2026-04-12
recorded_at: 2026-04-12T10:51:00.778Z
project: vpn-reality
topic: windows-karing-tun-routing
source: agent
status: active
---
# Verification Result

## Scope

Windows client migration to Karing + TUN with split routing

## Steps

- На Windows установлен Karing и профиль Reality импортирован через clipboard/file.
- Karing запущен от администратора, TUN активен.
- В Karing Connect подтверждено: ya.ru/Яндекс Музыка идут Direct.
- В Karing Connect подтверждено: Steam traffic (store.steampowered.com, api.steampowered.com, steamstatic CDN) идёт через final -> reality-main-desktop-windows-public-ipv4.
- Подтверждено пользователем: домен из ru-blocked идёт через final.
- Telegram Desktop исключён из обязательной проверки TUN, так как использует отдельный MTProto-контур.

## Result

Проверка пройдена. Karing на Windows корректно поднимает TUN, process-aware routing работает, direct и final реально различаются. Российские локально доступные сервисы идут direct, обычный внешний desktop-трафик и ru-blocked трафик идут через VPN-маршрут final. Это подтверждает, что миграция с v2rayN System Proxy на Karing + TUN технически состоялась.
