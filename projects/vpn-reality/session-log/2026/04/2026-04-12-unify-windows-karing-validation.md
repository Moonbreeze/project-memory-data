---
date: 2026-04-12
recorded_at: 2026-04-12T10:51:00.927Z
project: vpn-reality
topic: unify-windows-karing-validation
source: agent
status: active
---
# Session Note

## Summary

Живая валидация Windows-клиента завершена: Karing + TUN подтверждён на реальном трафике, split routing различает direct и final, Steam уходит в final, российские сервисы идут direct, ru-blocked подтверждён через VPN.

## Actions

- Пользователь подтвердил, что Telegram не является частью VPN-критерия, так как использует отдельный MTProto.
- По экрану Karing Connect подтверждено, что process-aware accounting работает: видны steamwebhelper.exe, vivaldi.exe, Яндекс Музыка.exe.
- Интерпретирован маршрут final как итоговый VPN-маршрут для трафика, не попавшего в direct/special rules; для Steam это нормальное поведение.
- Пользователь подтвердил, что домен из ru-blocked уходит через final.
- Сделан вывод, что миграция Windows-клиента на Karing + TUN состоялась и Telegram не является блокером завершения work-item.

## Follow-up

- Суперсидировать decision windows-system-proxy-over-tun новым decision.
- Закрыть work-item unify-windows-hiddify-next после обновления evidence.
- При желании позже завести отдельный work-item для Android split routing и/или fine-tuning per-app direct rules на Windows.
