---
date: 2026-04-18
recorded_at: 2026-04-18T12:37:54.539Z
project: vps-bootstrap
topic: repo-validation
source: agent
status: active
---
# Runbook

## Purpose

Проверять, что репозиторий vps-bootstrap в валидном базовом состоянии после изменений в bootstrap-скрипте, тестах или ai-inst конфигурации.

## Procedure

- Запустить `bash -n ./bootstrap.sh` в корне репозитория.
- Запустить `./tests/bootstrap.test.sh` для shell-based smoke coverage без мутаций хоста.
- Если менялись ai-inst правила или `.ai-modules`, выполнить `ai-inst build` и убедиться, что `AGENTS.md` и `CLAUDE.md` пересобраны без ошибок.
- Проверить `git status --short`, чтобы увидеть новые или изменённые артефакты после сборки и тестов.

## Verification

- `bash -n ./bootstrap.sh` завершается с кодом 0.
- `./tests/bootstrap.test.sh` печатает `bootstrap tests passed`.
- `ai-inst build` успешно генерирует `AGENTS.md` и `CLAUDE.md` при изменениях в правилах.
