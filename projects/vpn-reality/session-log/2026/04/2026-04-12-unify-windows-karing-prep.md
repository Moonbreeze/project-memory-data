---
date: 2026-04-12
recorded_at: 2026-04-12T10:02:17.746Z
project: vpn-reality
topic: unify-windows-karing-prep
source: agent
status: active
---
# Session Note

## Summary

Подтверждены по официальным источникам ключевые свойства Karing для work-item unify-windows-hiddify-next: Windows TUN требует запуска от администратора, импорт профиля возможен из clipboard/file, а custom diversion поддерживает remote rule-set в форматах .srs/.json по raw URL. Это снимает продуктовый риск на уровне документации, но не заменяет живую валидацию на Windows.

## Actions

- Проверены официальные страницы Karing App Manual: Add Profiles, Settings, Policy and diversion, Custom diversion group editing.
- Подтверждено: Add Profiles принимает v2ray/sing-box профили, поддерживает Import from Clipboard и Import Profile File; локальные profile files не обновляются автоматически.
- Подтверждено: TUN на Windows поддерживается, но Karing нужно запускать от администратора.
- Подтверждено: custom diversion group принимает remote rule-set по URL с расширением .srs или .json; для GitHub нужно использовать raw URL.
- Проверен официальный README репозитория Karing и README репозитория KaringX/karing-ruleset: проект позиционируется как sing-box GUI, а в секции russia явно указано использование источников runetfreedom/russia-v2ray-rules-dat и перечислены rule-set'ы blocked@ru.srs, blocked-community@ru.srs, available-only-inside@ru.srs.
- Зафиксировано ограничение из KaringX/karing-ruleset: крупные SRS-файлы (>3M) рекомендованы только для Windows, на Android/iOS возможны memory-limit проблемы.

## Follow-up

- На Windows установить Karing и проверить реальный happy path: импорт одиночной vless:// ссылки, создание custom diversion groups, подключение remote .srs rule-set'ов runetfreedom, включение TUN от администратора.
- Проверить конкретные URL runetfreedom в Karing UI через Diversion Rule Detection и убедиться, что geosite blocked@ru и geoip blocked-community@ru реально скачиваются и матчятся.
- После живой валидации обновить canonical-doc clients.md и runbook add-device.md, затем суперсидировать decision windows-system-proxy-over-tun новым decision.
