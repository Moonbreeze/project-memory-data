---
date: 2026-04-12
recorded_at: 2026-04-12T16:59:00.891Z
project: vpn-reality
topic: remove-nopasswd-sudo
source: user
status: active
---
# Verification Result

## Scope

Removal of temporary nopasswd sudoers entry on current machine

## Steps

- Подтверждено, что `/etc/sudoers.d/` больше не содержит `moonbreeze-nopasswd`.
- Подтверждено, что `sudo -n true` возвращает ошибку `sudo: a password is required`.
- Пользователь вручную запустил `sudo visudo -c` после удаления файла.

## Result

Проверка пройдена. Временный sudoers drop-in удалён, sudo снова требует пароль, `sudo visudo -c` завершился с `parsed OK`.
