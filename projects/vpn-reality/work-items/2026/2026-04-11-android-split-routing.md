---
date: 2026-04-11
recorded_at: 2026-04-11T16:25:06.297Z
project: vpn-reality
topic: android-split-routing
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Перевести Android-клиент со схемы Hiddify-only на Karing + TUN и настроить split routing: российские сервисы напрямую, ru-blocked и внешний трафик через туннель.

## Outcome

Android-клиент ведёт себя симметрично Windows: локально доступные российские сервисы открываются с российского IP, а ru-blocked и внешний трафик идут через DE-exit по relay-first профилю.

## Provenance

- ad-hoc: Сейчас на Android весь трафик идёт через тоннель, из-за чего локально доступные российские сайты ломаются при включённом VPN.

## Dependencies

- none

## Context

- decision:vpn-reality:2026-04-12:android-karing-over-hiddify-for-split-routing
- canonical-doc:vpn-reality:client-setup:clients

## Verification

- Karing на Android установлен, relay-first профиль импортирован через clipboard/file, системное VPN-разрешение выдано.
- В Karing выставлен корректный `Country Or Region`, включён `Private network direct connection`, группа `ru-blocked` активна с remote runetfreedom .srs rule-set'ами.
- ya.ru на Android с включённым VPN открывается и показывает российский IP.
- Заблокированный в РФ домен открывается через туннель.
- После живой проверки записан отдельный verification-result по Android routing.

## Evidence

- session-note:vpn-reality:2026-04-12:android-split-routing-decision-and-docs
- session-note:vpn-reality:2026-04-12:android-split-routing-live-validation
- verification-result:vpn-reality:2026-04-12:android-karing-split-routing
