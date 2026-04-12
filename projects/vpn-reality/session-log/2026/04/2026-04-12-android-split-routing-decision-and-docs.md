---
date: 2026-04-12
recorded_at: 2026-04-12T15:16:12.780Z
project: vpn-reality
topic: android-split-routing-decision-and-docs
source: agent
status: active
---
# Session Note

## Summary

Android split routing переведён из Hiddify-backlog в рабочую проектную схему на Karing + TUN; обновлены decision, canonical guidance и runbook add-device.

## Actions

- Подтверждён проектный разворот: для Android split routing используется Karing + sing-box + TUN, а Hiddify-Next остаётся только fallback без custom split routing.
- Создан decision `android-karing-over-hiddify-for-split-routing`, который фиксирует отказ от Hiddify как primary Android split-routing клиента.
- Обновлён canonical-doc `client-setup/clients.md`: Android и Windows теперь описаны через единый Karing-based стек.
- Переписан runbook `add-device.md` под Android/Windows через Karing, с `Country Or Region`, `Private network direct connection` и remote runetfreedom .srs rule-set'ами для группы `ru-blocked`.
- Work-item `android-split-routing` переведён в `in_progress` и переписан под реальную задачу миграции и живой Android-валидации.

## Follow-up

- На реальном Android-устройстве пройти runbook: импорт профиля, выдать VPN permission, включить routing и проверить `ya.ru` plus домен из `ru-blocked`.
- После живой проверки записать отдельный verification-result по Android routing и добавить его в evidence work-item `android-split-routing`.
