---
date: 2026-04-12
recorded_at: 2026-04-12T16:57:22.750Z
project: vpn-reality
topic: remove-nopasswd-sudo
source: agent
status: active
---
# Session Note

## Summary

На текущей машине удалён `/etc/sudoers.d/moonbreeze-nopasswd`; подтверждено, что `sudo -n true` снова требует пароль. Финальная проверка `visudo -c` упёрлась в обычный sudo prompt после удаления NOPASSWD.

## Actions

- Найден локальный файл `/etc/sudoers.d/moonbreeze-nopasswd` с содержимым `moonbreeze ALL=(ALL) NOPASSWD:ALL`.
- Файл `/etc/sudoers.d/moonbreeze-nopasswd` удалён через sudo вне sandbox.
- Проверено, что `/etc/sudoers.d/` больше не содержит `moonbreeze-nopasswd`.
- Проверено, что `sudo -n true` возвращает `sudo: a password is required`.

## Follow-up

- Запустить `sudo visudo -c` с обычным локальным паролем пользователя и, если конфиг валиден, закрыть work-item `remove-nopasswd-sudo`.
