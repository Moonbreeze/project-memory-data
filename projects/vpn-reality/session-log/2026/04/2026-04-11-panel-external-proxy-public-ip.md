---
date: 2026-04-11
recorded_at: 2026-04-11T17:44:18.935Z
project: vpn-reality
topic: panel-external-proxy-public-ip
source: agent
status: active
---
# Session Note

## Summary

Убран ручной шаг замены 127.0.0.1 → 147.45.196.137 в share-ссылках 3x-ui через настройку External Proxy entry на inbound reality-main. Побочная задача, всплывшая во время планирования work-item unify-windows-hiddify-next: обсуждали, действительно ли для разблокировки надо выносить панель наружу (work-item panel-domain-and-le-cert), и в процессе пользователь задал вопрос про альтернативы без выноса — оказалось, что 3x-ui 2.8.x поддерживает External Proxy override на уровне inbound, и это решает ровно исходную боль без изменения security-посture.

## Actions

- Обсудили и переформулировали скоп work-item unify-windows-hiddify-next под файловую доставку профиля (без subscription-URL).
- Зафиксировали decision profile-file-over-subscription-url; work-item panel-domain-and-le-cert переведён в canceled/archived с указанием триггеров для пересоздания (user-base ≥5 или квартальная ротация ключей).
- Проведен research-гейт по runetfreedom: подтверждено наличие .srs файлов в russia-blocked-geoip (путь release/srs/, авто-обновление раз в 6ч). Сомнение: репа называется GeoIP, то есть ru-blocked.srs там, вероятно, IP-based, а не domain-based. Domain-based .srs в russia-blocked-geosite не публикуется. Допроверка вынесена в follow-up.
- Побочная задача: по вопросу пользователя разобрали возможность правильного IP в share-ссылках без выноса панели.
- В панели 3x-ui добавлен External Proxy entry на inbound reality-main (Forced Expose IP = 147.45.196.137, Port = 443, Remark = public-ipv4). Никакие другие поля формы не трогались.
- Из списка клиентов скопирован URL для phone-android и визуально сверен: хост 147.45.196.137, все 9 Reality-параметров на месте, подробности в verification-result panel-external-proxy-public-ip.
- Обновлён runbook add-client (убран шаг ручной замены хоста, добавлена sanity-check ссылки на External Proxy entry при обнаружении 127.0.0.1).
- Обновлён canonical-doc infrastructure/topology (булет про External Proxy override вместо старого про ручную замену 127.0.0.1; добавлена ссылка на decision profile-file-over-subscription-url и на verification-result).

## Follow-up

- Доверифицировать клиентский `curl ifconfig.me` после импорта обновлённой ссылки в v2rayN/Hiddify — привязать к исполнению work-item unify-windows-hiddify-next, где всё равно будет перенастраиваться Windows-клиент.
- Допроверить, содержит ли ru-blocked.srs из russia-blocked-geoip только ip_cidr правила, или в нём есть и domain_suffix. Реализация: скачать `.srs` и прогнать через `sing-box rule-set decompile` (JSON-ответ покажет тип rules). От результата зависит, нужна ли локальная компиляция domain-based правил из russia-blocked-geosite.
- Рассмотреть, убирать ли суффикс `-public-ipv4` из remark External Proxy entry (можно оставить пустым). Косметически, не критично.
- В decision ssh-tunnel-over-le один из consequences (ручная замена 127.0.0.1 в ссылках) стал устаревшим. Решение: не редактировать исторический decision-документ; текущая правда отражена в canonical-doc topology и runbook add-client.
