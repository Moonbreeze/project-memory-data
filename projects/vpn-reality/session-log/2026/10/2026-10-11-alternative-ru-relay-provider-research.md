---
date: 2026-10-11
recorded_at: 2026-10-11T08:44:22.925Z
project: vpn-reality
topic: alternative-ru-relay-provider-research
source: agent
status: active
---
# Session Note

## Summary

Проведено read-only сравнение Selectel, VDSina и Timeweb Cloud для независимого от Yandex RU entry. Предварительный предпочтительный вариант: Selectel VDS 1-2-25 за опубликованные 250 ₽/мес.; окончательный выбор и проверка сети ещё не выполнены.

## Actions

- Требования сверены с topology: Xray public TCP443 -> DE TCP8443; HAProxy TCP9443 -> приватный DE mtg через исходящий WireGuard UDP51820.
- Selectel официальный тариф https://selectel.ru/services/cloud/vps-vds/ публикует 1vCPU/1GB/10GB за 200 ₽/мес. и 1vCPU/2GB/25GB за 250 ₽/мес.; публичный IPv4 включён по документации; Москва/СПб, Ubuntu22/24 и KVM подтверждены.
- Selectel https://docs.selectel.ru/vds-servers/about/payment/ предоставляет 3ТБ внешнего RX+TX в месяц на все проекты аккаунта. Relay примерно удваивает учтённый объём относительно пользовательских данных. Published port restrictions не перечисляют необходимые 443/8443/9443/51820; фактический маршрут не тестирован.
- VDSina https://vdsina.ru/pricing/standard публикует 1vCPU/1GB/10GB/1ТБ за 5 ₽/день (150 ₽ за 30дней), 1vCPU/2GB/50GB/32ТБ за 20 ₽/день (600 ₽ за 30дней), превышение 200 ₽/ТБ. Москва доступна, предлагаются VPN/WireGuard/3proxy images; https://vdsina.ru/qa/q/tarifikatsiya-vkhodyashchego-i-iskhodyashego-trafika подтверждает общий трафик. Включение основного IPv4 в цену требует проверки при заказе.
- Timeweb https://timeweb.cloud/services/vds-vps публикует Cloud-15 1vCPU/1GB/15GB за 1380 ₽/мес. с 1Гбит/с, бесплатным безлимитным трафиком с fair-use условиями. IPv4 оплачивается почасово, цена доступна только при заказе: https://timeweb.cloud/docs/public-ip. Полный итог VM+IPv4 не подтверждён.
- Текущие AUP для точного закрытого VLESS/MTProto relay нужно уточнить у поддержки перед оплатой; сетевую доступность DE, стабильность handshake и мобильных клиентов на новых IP необходимо тестировать.
- Ничего не приобретено и не развёрнуто. Topology и provider notes не менялись, поскольку новый провайдер не выбран.

## Follow-up

- Получить выбор пользователя и подтверждение AUP; заказать небольшую RU VM без долгосрочной предоплаты.
- С нового узла проверить маршрут к DE, REALITY www.cloudflare.com и WireGuard; разрешить новый relay IP на DE:8443/51820 только адресно.
- Для параллельного второго MTProto relay использовать отдельный WG peer и непересекающийся приватный адрес/подсеть с проверенной HAProxy/mtg связностью; не назначать обоим relay один AllowedIP 10.66.0.1.
- Сгенерировать новый public Reality profile; для Telegram сменить endpoint в ссылке, сохраняя secret только если FakeTLS hostname не меняется. Проверить действующую зависимость FakeTLS от cloud.yandex.ru.
- Оставить temporary-direct-de до успешной проверки обоих новых relay-first контуров на реальных устройствах.
