---
date: 2026-06-02
recorded_at: 2026-06-02T16:47:42.716Z
project: english-assistant
topic: production-domain-routing-and-smoke
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Настроить production domain routing для лендинга и приложения и проверить end-to-end работу после deploy.

## Outcome

Root-domain в production отдаёт лендинг, assistant subdomain продолжает отдавать приложение, а обе поверхности обновляются через общий push-triggered deploy.

## Provenance

- ad-hoc: Подключение production root-domain к лендингу при сохранении assistant subdomain за приложением.

## Dependencies

- work-item:english-assistant:2026-06-02:multi-service-build-and-deploy-integration

## Context

- none

## Verification

- <root-domain> открывает лендинг.
- www.<root-domain> открывает лендинг или делает корректный redirect на канонический host.
- assistant.<root-domain> открывает текущее приложение.
- CTA с лендинга ведёт в приложение.
- После тестового push обновления доходят до обеих поверхностей.

## Evidence

- none
