---
date: 2026-03-14
project: ai-inst
topic: bug-registry-project-memory-view
source: user
status: active
---
# Decision

## Context

Модуль ai-inst testing задаёт правило: реестр известных багов ведётся в src/__tests__/KNOWN_BUGS.md, каждый баг покрывается тестом с комментарием // Bug #N. Решение bug-registry-source-of-truth (claude-remote) зафиксировало этот файл как canonical source. Возник вопрос, стоит ли перенести реестр целиком в project-memory как часть проектной документации. Полное перемещение создаёт риск рассинхрона между реестром и тестами, поскольку связь баг↔тест требует co-location в репозитории.

## Decision

Реестр багов в репозитории (KNOWN_BUGS.md + тесты с // Bug #N) остаётся canonical source of truth. Project-memory может хранить агрегированный обзор активных багов как производную проекцию — для cross-project видимости и быстрого старта сессий. При расхождении приоритет у репозитория.

## Consequences

- Модуль testing не меняется — правило о KNOWN_BUGS.md и покрывающих тестах сохраняется
- Агрегированный обзор в project-memory обновляется по мере необходимости, не синхронно с каждым коммитом
- При появлении canonical-doc обзор может быть оформлен как canonical-doc с соответствующим scope
- Решение bug-registry-source-of-truth (claude-remote) остаётся валидным и согласованным
