---
date: 2026-10-11
recorded_at: 2026-10-11T21:24:08.766Z
project: vpn-reality
topic: ruhop-windows-link-tooling
source: user
status: active
---
# Verification Result

## Scope

Windows-native committed-HEAD delivery and one-command retrieval of VLESS/MTProto client links for the VDSina relay.

## Steps

- Локальная suite vpn-relay-bootstrap: 53 tests passed, один root-зависимый wg-quick parser test skipped; deliver shell tests, Bash syntax and diff checks passed.
- Пользователь запустил `deliver.ps1 ruhop` и подтвердил доставку committed HEAD без запуска bootstrap.
- Пользователь запустил `get-links.ps1`; VLESS link успешно создан на ruhop и передан на Windows.
- Live metadata подтвердили `/etc/mtg.toml` mode 0640 owner root group mtg и systemd mtg User/Group mtg без DynamicUser.
- После узкого permission fix пользователь повторил `get-links.ps1` и подтвердил успешное получение обеих ссылок.
- Содержимое VLESS UUID, Reality credentials и MTProto secret не передавалось в чат или project-memory.

## Result

Проверка пройдена. Из корня Windows checkout одна явная команда получает рабочие VLESS и MTProto links через aliases ruhop/dev; committed helper guard и permission checks сохраняют установленные security boundaries.
