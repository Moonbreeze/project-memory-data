---
date: 2026-03-12
project: ai-inst
topic: skills-implementation
source: imported
status: active
---
# Runbook

## Purpose

Пошаговый план реализации системы навыков (skills) в ai-inst — CLI, MCP, тесты.

## Procedure

- Шаг 1: Переменные и helpers — добавить SKILLS_DIR="$AI_INST_DIR/skills", helpers: skill_path, skill_exists, skill_description (извлечение description из YAML frontmatter SKILL.md). Обновить parse_ai_modules для секции [skills] (возвращать TARGETS, MODULES, SKILLS).
- Шаг 2: CLI-команды skill — skill new <name> (создание директории + SKILL.md шаблон + $EDITOR + коммит), skill list (итерация по skills/, маркер * для активных в проекте), skill show <name> (вывод SKILL.md), skill edit <name> ($EDITOR + коммит), skill rm <name> (удаление директории + коммит).
- Шаг 3: CLI-команды project — project add-skill <name...> (проверка существования навыка, добавление в [skills], создание секции если нет), project rm-skill <name...> (удаление из [skills]). Обновить project status для отображения навыков.
- Шаг 4: Расширение build — очистка .claude/skills/ и .agents/skills/ перед копированием. Копирование директорий навыков as-is в оба пути. Генерация индекса навыков (## Available skills) в целевых файлах с description из frontmatter. Добавление .claude/skills/ и .agents/skills/ в .gitignore.
- Шаг 5: Обновление repo init — создание $AI_INST_DIR/skills/ при ai-inst repo init.
- Шаг 6: MCP-сервер — добавить tools: list_skills, read_skill, create_skill, update_skill, delete_skill, add_project_skill, remove_project_skill. Аналогично существующим module-tools, оборачивают CLI.
- Шаг 7: Тесты — helper create_skill(). Тесты skill (new, duplicate, show, missing, rm, list, list_with_project_markers). Тесты project (add_skill, creates_section, duplicate, rm_skill). Тесты build (copies_to_claude_dir, copies_to_agents_dir, directory_structure, skills_index, cleans_old, gitignore, missing_warning).
- Шаг 8: Help и README — обновить cmd_help() секциями Skills и Project. Обновить README: архитектура, примеры, справка по командам.

## Verification

- Все существующие тесты (55 шт.) проходят — обратная совместимость не нарушена
- Все новые тесты навыков проходят: bash tests/test_cli.sh
- Формат .ai-modules без [skills] работает как раньше
- Build копирует навыки в .claude/skills/ и .agents/skills/
- Индекс навыков с description появляется в целевых файлах
- .gitignore обновлён для сгенерированных директорий
