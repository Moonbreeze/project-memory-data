---
date: 2026-04-11
recorded_at: 2026-04-11T16:25:06.877Z
project: vpn-reality
topic: remove-nopasswd-sudo
source: agent
status: active
work_item_state: in_progress
---
# Work Item

## Summary

Удалить временный /etc/sudoers.d/moonbreeze-nopasswd на DE-exit VPS, который был добавлен только для установки 3x-ui без TTY.

## Outcome

sudo снова требует пароль; поверхность атаки уменьшена.

## Provenance

- ad-hoc: Введён во время Этапа 2 как временный обход sudo без TTY через `!`.

## Dependencies

- none

## Context

- none

## Verification

- `ls /etc/sudoers.d/` не содержит moonbreeze-nopasswd.
- `sudo -n true` возвращает ошибку (пароль требуется).
- `visudo -c` зелёный.

## Evidence

- session-note:vpn-reality:2026-04-12:remove-nopasswd-sudo
