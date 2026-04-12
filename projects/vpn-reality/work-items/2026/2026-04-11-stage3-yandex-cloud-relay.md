---
date: 2026-04-11
recorded_at: 2026-04-11T16:24:59.120Z
project: vpn-reality
topic: stage3-yandex-cloud-relay
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Поднять промежуточный relay-узел на Yandex Cloud (чистая Ubuntu) как второй слой из оригинальной статьи Habr 1021160 — цепочка client → RU-relay → DE-exit.

## Outcome

Трафик клиентов идёт через RU-relay (снижает задержки, маскирует зарубежный IP на первом хопе), а финальный exit остаётся на 147.45.196.137.

## Provenance

- ad-hoc: Из общего плана: Этап 3 исходной Habr-статьи про relay-цепочку. Отложен до успешного Этапа 2.

## Dependencies

- none

## Context

- none

## Verification

- curl ifconfig.me с клиента возвращает немецкий IP.
- tcpdump на relay показывает входящий VLESS и исходящее соединение к DE-exit.
- Задержка до ya.ru с клиента через VPN сопоставима с прямой.

## Evidence

- session-note:vpn-reality:2026-04-12:stage3-yandex-cloud-relay
- verification-result:vpn-reality:2026-04-12:stage3-yandex-cloud-relay
