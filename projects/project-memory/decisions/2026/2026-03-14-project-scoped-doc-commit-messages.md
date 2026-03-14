---
date: 2026-03-14
project: project-memory
topic: project-scoped-doc-commit-messages
source: agent
status: active
---
# Decision

## Context

История `project-memory-data` уже показала, что commit message в формате `docs(<scope>): <summary>` недостаточно информативен для managed-doc репозитория. Один и тот же scope встречается в разных проектах, а при разборе истории важен прежде всего проект, к которому относится запись. Дополнительно стало видно, что автоматизация будет проще и безопаснее, если целевой unit commit по умолчанию ограничен одним проектом и одной логической write-операцией.

## Decision

Для managed-doc коммитов в `project-memory-data` использовать формат `docs(<project>/<scope>): <summary>`. Проект становится обязательной частью commit message, а автоматизированные commit flows в `project-memory` должны по умолчанию формировать single-project commits и считать cross-project commits исключением, требующим отдельного осознанного пути.

## Consequences

- История managed-doc репозитория становится сразу читаемой по проектам без дополнительного просмотра diff.
- Текущая логика commit-scope в `project-memory` требует следующей реализации: добавить project-aware commit parsing, validation и scope inference для managed-doc changes.
- Автоматический commit после managed write-операций становится проще проектировать, потому что проект можно выводить из изменённых путей и запрещать нежелательные cross-project batches по умолчанию.
- Редкие multi-project commits остаются возможными только как отдельный явный режим, а не как поведение по умолчанию.
