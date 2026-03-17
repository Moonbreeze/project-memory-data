---
date: 2026-03-17
recorded_at: 2026-03-17T00:00:00.000Z
project: english-assistant
topic: bootstrap-client
source: agent
status: active
---
# Session Note

## Summary

Поднят клиент-пакет: Vite + React 19 + Redux Toolkit. Настроен proxy /api → localhost:3000, tsconfig с moduleResolution: bundler и jsx: react-jsx. tsc и vite build проходят.

## Actions

- Создан vite.config.ts с proxy /api на сервер (порт 3000)
- Создан index.html как точка входа Vite
- Создан src/main.tsx — React root с StrictMode и Redux Provider
- Создан src/app.tsx — корневой компонент-заглушка
- Создан src/store/index.ts — Redux store с типизированными RootState и AppDispatch
- Обновлён packages/client/package.json — добавлены react, react-dom, @reduxjs/toolkit, react-redux, vite, @vitejs/plugin-react; скрипты dev/build/preview
- Обновлён packages/client/tsconfig.json — module: ESNext, moduleResolution: bundler, jsx: react-jsx
- Добавлен esbuild в onlyBuiltDependencies корневого package.json
- Удалена старая заглушка src/index.ts

## Follow-up

- Добавить роутинг (react-router)
- Выбрать CSS-решение (CSS modules / Tailwind / etc.)
- Первые страницы и фичи
