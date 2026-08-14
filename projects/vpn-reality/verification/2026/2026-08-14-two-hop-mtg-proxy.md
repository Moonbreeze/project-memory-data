---
date: 2026-08-14
recorded_at: 2026-08-14T07:09:43.613Z
project: vpn-reality
topic: two-hop-mtg-proxy
source: agent
status: active
---
# Verification Result

## Scope

Двуххоповый Telegram MTProto path client -> Yandex relay:9443 -> WireGuard -> DE mtg -> Telegram

## Steps

- На DE проверены active/enabled wg-quick@wg-mtg и mtg services.
- Проверено, что DE имеет 10.66.0.2/30, WireGuard слушает 51820/udp, а mtg v2.2.8 слушает только 10.66.0.2:3128.
- С DE выполнен ping 10.66.0.1 с нулевой потерей и задержкой около 44 мс; на обоих peers подтверждён свежий WireGuard handshake и двусторонний transfer.
- На relay HAProxy успешно провалидирован и слушает 0.0.0.0:9443; после firewall fix backend de_mtg перешёл в UP с Layer4 check около 44 мс.
- С DE подтверждена публичная TCP-достижимость 178.154.193.39:9443.
- Пользователь импортировал tg://proxy endpoint 178.154.193.39:9443 и подтвердил успешное подключение Telegram после краткого начального статуса недоступности.

## Result

Проверка пройдена. Постоянный двуххоповый MTProto proxy работает через отдельный WireGuard transport и закрытый DE backend; существующий Xray Reality endpoint на relay:443 не изменён. Остаточный пробел: длительная media/restart проверка отдельно не проводилась.
