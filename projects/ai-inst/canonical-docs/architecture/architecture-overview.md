---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: ai-inst
topic: architecture-overview
registry_scope: architecture
source: agent
status: active
---
# Canonical Doc

## Summary

Обзор архитектуры ai-inst: двухрепозиторная модель, CLI на bash, MCP-сервер на TypeScript, система модулей/навыков/миграций, build pipeline

## Guidance

- **Двухрепозиторная модель**: tool repo (ai-inst CLI + MCP) — неизменяемый инструмент; rules repo (~/.ai-instructions/) — пользовательские модули, навыки, миграции, синхронизируемые через git
- **Rules repo структура**: modules/*.md (всегда в контексте), skills/<name>/SKILL.md (on-demand, Agent Skills стандарт), migrations/*.yml (автообновление .ai-modules), recommended (базовый набор модулей)
- **Проектная конфигурация (.ai-modules)**: targets: строка задаёт выходные файлы (по умолчанию CLAUDE.md), строки модулей до [skills], секция [skills] для навыков
- **Build pipeline**: загрузка .ai-modules → применение миграций → конкатенация модулей → генерация индекса навыков → добавление instructions.local.md → запись в target-файлы + копирование навыков в .claude/skills/ и .agents/skills/
- **CLI (bash, ~1600 строк)**: команды repo (init/clone/sync), module (list/new/edit/show/rm), skill (аналогично), project (init/add/rm/add-skill/rm-skill/status/doctor/targets), build, migrate, recommend (list/add/rm), hook (install/remove), mcp (install)
- **MCP-сервер (TypeScript, @modelcontextprotocol/sdk)**: оборачивает CLI-команды через execSync, ~23 инструмента, транспорт stdio. Установка через ai-inst mcp install --claude/--codex [--global]
- **Миграции**: YAML-файлы с when/then правилами (has_module/has_skill → add_module/remove_module/add_skill/remove_skill). Идемпотентны, состояние в .ai-migrations-state. Применяются автоматически при build
- **Recommended modules**: файл recommended в rules repo, команда project doctor проверяет наличие рекомендованных модулей в проекте
- **Контекстные слои**: modules = always-active baseline, skills = on-demand (индексируются, не встраиваются), instructions.local.md = project-specific overrides
- **Платформо-агностичность**: навыки копируются в .claude/skills/ (Claude Code) и .agents/skills/ (Codex, Cursor и др.), следуя стандарту Agent Skills (agentskills.io)

## References

- CLI: /home/moonbreeze/ai-inst/ai-inst
- MCP server: /home/moonbreeze/ai-inst/mcp-server/src/index.ts
- Rules repo: ~/.ai-instructions/
- Decision: skills-architecture (2026-03-12)
- Decision: subagents-as-separate-entity (2026-03-14)
- Runbook: skills-implementation
