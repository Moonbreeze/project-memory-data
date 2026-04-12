---
date: 2026-04-12
recorded_at: 2026-04-12T15:32:33.262Z
project: vpn-reality
topic: relay-threat-model-clarification
source: agent
status: active
---
# Session Note

## Summary

Уточнена security-model интерпретация relay-first схемы: Yandex relay уменьшает заметность первого хопа и разделяет entry/egress, но не считается исправлением клиентской localhost-proxy уязвимости на мобильном устройстве.

## Actions

- Проверена статья runetfreedom от 2026-04-07 про localhost SOCKS/VpnService bypass и сопоставлена с текущей relay-first архитектурой проекта.
- Зафиксировано, что Android-клиент следует считать потенциально компрометируемым по exit IP; выбор клиента сам по себе не считается достаточной защитой от hostile app на том же устройстве.
- Обновлён canonical-doc `security-model.md`: relay описан как mitigation against obvious first-hop exposure, а не как fix для mobile localhost-proxy кейса.
- В canonical guidance добавлено явное различение между компрометацией `entry` и `egress`, а также зафиксирован follow-up путь через отдельный egress fingerprint вроде Cloudflare WARP при необходимости.

## Follow-up

- Если work-item `cloudflare-warp-outbound-chain` будет выполняться, использовать эту threat-model формулировку как rationale для изменения.
- При подготовке install guide не обещать пользователю, что Android client-side split routing сам по себе скрывает exit IP от вредоносных приложений на телефоне.
