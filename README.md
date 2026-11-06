# Vue 3 SPA Starter Template

Минималистичный, чистый и производительный стартовый шаблон для SPA на **Vue 3**. Без лишнего кода, демонстрационных счетчиков и бойлерплейта.

---

## 🚀 Стек

- **Vue 3.5+** (Composition API, `<script setup>`)
- **TypeScript** (строгий режим + `vue-tsc` для валидации типов)
- **Vite** (быстрый HMR и сборка)
- **Tailwind CSS v4** (`@tailwindcss/vite`)
- **Vue DevTools** (`vite-plugin-vue-devtools` встроенная панель инспекции)
- **Vue Router 5 & Pinia** (готовы к использованию при добавлении страниц и стейта)
- **oxlint** (ультрабыстрый линтер на Rust)
- **oxfmt** (ультрабыстрый форматтер на Rust с авто-сортировкой классов Tailwind и импортов)
- **Lefthook** (быстрый pre-commit хук для typecheck, lint и format)
- **Bun** (пакетный менеджер)

---

## 📁 Структура проекта

```text
vue-template/
├── .vscode/                 # Рекомендации расширений для VS Code
├── public/                  # Favicon и статика
├── src/
│   ├── assets/              # main.css (@import "tailwindcss";)
│   ├── components/          # Компоненты приложения
│   ├── router/              # Конфиг Vue Router (заготовка)
│   ├── stores/              # Pinia хранилища
│   ├── App.vue              # Минимальный корневой компонент
│   └── main.ts              # Точка входа
├── index.html
├── lefthook.yml             # Конфигурация pre-commit хука
├── .oxlintrc.json           # Конфигурация oxlint
├── .oxfmtrc.json            # Конфигурация oxfmt
├── tsconfig.json            # TypeScript конфиг
├── vite.config.ts           # Vite конфиг (Vue, DevTools, Tailwind)
└── package.json
```

---

## 🛠 Команды

```bash
bun run dev          # Запуск сервера разработки (с Vue DevTools)
bun run build        # Проверка типов (vue-tsc) + production сборка
bun run typecheck    # Проверка типов
bun run lint         # Проверка oxlint
bun run lint:fix     # Автоисправление oxlint
bun run format       # Форматирование через oxfmt
bun run format:check # Проверка форматирования oxfmt
```
