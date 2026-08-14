---
date: 2026-08-14
recorded_at: 2026-08-14T07:10:44.920Z
project: vpn-reality
topic: two-hop-mtg-over-dedicated-wireguard
source: agent
status: active
---
# Decision

## Context

Проекту нужен постоянный Telegram MTProto proxy, использующий существующее разделение Yandex relay и DE exit. Рабочий Xray relay-first VPN уже занимает relay:443 и использует собственный VLESS Reality backhaul, который не является универсальным transport для стороннего TCP-сервиса. Публичный mtg на DE нарушил бы текущую security boundary, а размещение mtg только на relay убрало бы разделение entry/egress.

## Decision

Telegram MTProto proxy разворачивается как отдельный двуххоповый контур: клиент подключается к Yandex relay на 9443/tcp, HAProxy передаёт исходный client IP через PROXY protocol v2 по выделенному WireGuard wg-mtg, а mtg v2 слушает только приватный адрес DE 10.66.0.2:3128. Этот контур не переиспользует Xray backhaul и не меняет VLESS Reality endpoint relay:443.

## Consequences

- Плюс: публичный entry остаётся в Yandex Cloud, а Telegram egress выполняется с DE; entry и egress можно обслуживать независимо.
- Плюс: mtg backend не публикуется на DE и разрешён firewall только от relay через wg-mtg.
- Плюс: Xray Reality на 443/tcp и его VLESS backhaul остаются независимыми от MTProto-контура.
- Плюс: HAProxy передаёт реальный client IP через PROXY protocol v2, поэтому mtg blocklist не воспринимает все соединения как один RFC1918 source.
- Минус: добавляются WireGuard, HAProxy backend и отдельные firewall rules как дополнительные точки диагностики.
- Минус: внешний MTProto endpoint использует 9443/tcp, который может быть недоступен в сетях с разрешёнными только 80/443.
- Операционное ограничение: MTProto secret и WireGuard private keys нельзя сохранять в project-memory; FakeTLS hostname или secret меняются только с перевыдачей клиентских ссылок.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
