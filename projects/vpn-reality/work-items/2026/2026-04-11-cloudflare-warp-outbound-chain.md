---
date: 2026-04-11
recorded_at: 2026-04-11T16:25:03.252Z
project: vpn-reality
topic: cloudflare-warp-outbound-chain
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Навесить Cloudflare WARP как дополнительный outbound chain на DE-exit, чтобы финальный IP не был IP хостера Aeza.

## Outcome

Фингерпринт exit-узла перестаёт указывать на Aeza-диапазон; сайты с anti-VPN скорингом реже ругаются.

## Provenance

- ad-hoc: Идея из обсуждения улучшений после Этапа 2.

## Dependencies

- none

## Context

- none

## Verification

- ifconfig.me через VPN показывает Cloudflare ASN, не Aeza.
- Xray routing правила корректно матчат только нужные домены в WARP outbound.
- Скорость по fast.com не деградирует более чем на 30% относительно прямого exit.

## Evidence

- none
