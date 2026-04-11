---
date: 2026-04-11
recorded_at: 2026-04-11T16:25:06.297Z
project: vpn-reality
topic: android-split-routing
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Настроить split routing в Hiddify-Next на Android: ru-домены напрямую, заблокированные в РФ — через тоннель.

## Outcome

Android-клиент ведёт себя симметрично Windows: российские сайты открываются с российского IP, ru-blocked — через DE-exit.

## Provenance

- ad-hoc: Сейчас на Android весь трафик идёт через тоннель → ru-сайты ломаются при включённом VPN.

## Dependencies

- none

## Context

- none

## Verification

- ya.ru на Android с включённым VPN открывается и показывает российский IP.
- Заблокированный в РФ домен открывается через тоннель.
- Hiddify Routing содержит правила direct для geosite:geolocation-cn/ru и proxy для ru-blocked (или sing-box эквивалентов).

## Evidence

- none
