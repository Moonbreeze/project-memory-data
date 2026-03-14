---
date: 2026-03-14
project: ai-inst
topic: subagents-as-separate-entity
source: user
status: draft
---
# Decision

## Context

Рассмотрены три варианта добавления поддержки субагентов в ai-inst: (1) отдельная сущность agents/ по аналогии со skills, (2) подтип skills через поле type: agent в frontmatter, (3) без поддержки в ai-inst. Skills и agents семантически различны: skill — инструкция для основного агента, agent — отдельная роль с изолированным контекстом. Структура артефактов тоже отличается: skill — директория с ресурсами, agent — один markdown-файл.

## Decision

Субагенты реализуются как отдельная сущность (вариант 1): директория agents/ в rules-репо, секция [agents] в .ai-modules, CLI-команды agent list/new/show/edit/rm и project add-agent/rm-agent. Build копирует в .claude/agents/. Общая логика со skills извлекается в параметризованные функции. Реализация откладывается до появления реального use-case и стабилизации формата субагентов в платформах.

## Consequences

- Чистое разделение skills и agents — нет leaky abstraction
- Больше кода при реализации, но паттерн уже отработан на skills
- Миграции потребуют расширения: add_agent/remove_agent в when/then
- Риск: формат субагентов в платформах (Codex, Cursor) может измениться до момента реализации
