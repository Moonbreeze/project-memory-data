---
date: 2026-10-11
recorded_at: 2026-10-11T21:24:08.756Z
project: vpn-reality
topic: ruhop-client-link-tooling
source: agent
status: active
---
# Session Note

## Summary

В vpn-relay-bootstrap добавлены и проверены безопасные helpers для доставки проекта и получения VLESS/MTProto ссылок с Windows через существующие SSH aliases.

## Actions

- Добавлен `client_links.py`: VLESS links создаются на ruhop из приватного relay config и Reality keypair; MTProto link создаётся на DE из защищённого mtg config с публичным endpoint 138.16.175.166:9443.
- Добавлен `deliver.ps1`, доставляющий только committed HEAD через SSH alias без запуска bootstrap; пользователь подтвердил успешную доставку commit.
- Добавлен `get-links.ps1`: одной явной командой из корня проекта получает VLESS через `ruhop`, временно запускает committed standalone helper на `dev`, читает mtg secret через sudo и показывает обе ссылки.
- Temporary local/DE files удаляются в finally; VLESS-generated file остаётся mode 0600 на relay. Credentials выводятся только при явном `get-links.ps1` и остаются в terminal scrollback.
- Permission validation для `/etc/mtg.toml` согласована с live состоянием 0640 root:mtg и service User/Group mtg; group-write, иная группа и world access отклоняются.
- Пользователь подтвердил успешный финальный запуск `get-links.ps1`.
- Принята постоянная shared VLESS identity с label `ruhop-shared`; существующий UUID сохранён и не записан в документацию.

## Follow-up

- Не публиковать вывод get-links.ps1; при утечке ротировать общий VLESS UUID и раздать новый профиль всем пользователям.
- После согласованного 24-часового soak выполнить отдельную cleanup-задачу temporary direct-DE.
- При изменении alias, relay IPv4 или shared label обновить defaults get-links.ps1 и stable guidance.
