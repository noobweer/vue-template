# Vue 3 SPA Starter Template

Современный, минималистичный и ультрабыстрый шаблон для создания Single Page Application (SPA) на **Vue 3**.

Проект собран без лишнего бойлерплейта и мусора — чистая архитектура, строгий TypeScript, моментальный линтинг и форматирование на Rust, а также автоматические pre-commit хуки.

---

## 🚀 Стек технологий

- **Фреймворк**: [Vue 3.5+](https://vuejs.org/) (Composition API, `<script setup>`)
- **Язык**: [TypeScript](https://www.typescriptlang.org/) (строгий режим + `vue-tsc` для валидации типов)
- **Сборщик**: [Vite](https://vite.dev/) (мгновенный HMR и оптимизированный production-билд)
- **Стили**: [Tailwind CSS v4](https://tailwindcss.com/) (подключён через нативный `@tailwindcss/vite`, без лишних конфигов)
- **Маршрутизация**: [Vue Router 5](https://router.vuejs.org/) (клиентский SPA-роутинг с ленивой загрузкой)
- **Состояние**: [Pinia](https://pinia.vuejs.org/) (типобезопасный реактивный стейт-менеджмент)
- **Линтер**: [oxlint](https://oxc.rs/docs/guide/usage/linter) (сверхбыстрый линтер на Rust)
- **Форматтер**: [oxfmt](https://oxc.rs/docs/guide/usage/formatter) (форматтер на Rust с автоматической сортировкой классов Tailwind и импортов)
- **Git Hooks**: [Lefthook](https://github.com/evilmartians/lefthook) (параллельный запуск typecheck, oxlint и oxfmt перед коммитом за доли секунды)
- **Пакетный менеджер**: [Bun](https://bun.sh/) (поддерживаются также pnpm и npm)

---

## 📁 Структура проекта

```text
vue-template/
├── .github/                 # CI/CD воркфлоу (опционально)
├── .vscode/                 # Рекомендуемые расширения для VS Code (Volar, Oxc, Tailwind)
├── public/                  # Статические ассеты (favicon.svg и др.)
├── src/
│   ├── assets/              # Глобальные стили (main.css с подключением Tailwind v4)
│   ├── components/          # Переиспользуемые компоненты (BaseButton.vue и др.)
│   ├── router/              # Конфигурация Vue Router (index.ts)
│   ├── stores/              # Pinia хранилища (counter.ts)
│   ├── views/               # Страницы приложения (HomeView.vue, AboutView.vue)
│   ├── App.vue              # Корневой лейаут приложения
│   └── main.ts              # Точка входа приложения
├── env.d.ts                 # Декларации типов для Vite
├── index.html               # Точка монтирования SPA
├── lefthook.yml             # Конфигурация pre-commit хуков
├── .oxlintrc.json           # Конфигурация oxlint
├── .oxfmtrc.json            # Конфигурация oxfmt
├── tsconfig.json            # Корневой конфиг TypeScript
├── tsconfig.app.json        # Конфиг TypeScript для исходников приложения (@/ -> src/)
├── tsconfig.node.json       # Конфиг TypeScript для vite.config.ts
├── vite.config.ts           # Конфигурация Vite (@tailwindcss/vite, alias @)
└── package.json             # Скрипты и зависимости
```

---

## ⚡ Быстрый старт

### 1. Установка зависимостей

```bash
bun install
```

> **Примечание**: хуки `lefthook` настраиваются автоматически при выполнении команды `bun install` благодаря хуку `postinstall`.

### 2. Запуск локального сервера разработки

```bash
bun run dev
```

Приложение откроется по адресу `http://localhost:5173/`.

### 3. Сборка для production

```bash
bun run build
```

Команда сначала проверяет типы с помощью `vue-tsc --noEmit`, а затем собирает оптимизированный бандл в директорию `dist/`.

---

## 🛠 Доступные скрипты

| Скрипт                 | Описание                                                     |
| :--------------------- | :----------------------------------------------------------- |
| `bun run dev`          | Запуск dev-сервера Vite с горячей перезагрузкой (HMR)        |
| `bun run build`        | Полная проверка типов (`vue-tsc`) и сборка production-бандла |
| `bun run preview`      | Локальный просмотр собранного production-билда               |
| `bun run typecheck`    | Проверка типов всего проекта без генерации файлов            |
| `bun run lint`         | Запуск линтера `oxlint`                                      |
| `bun run lint:fix`     | Автоматическое исправление ошибок через `oxlint --fix`       |
| `bun run format`       | Форматирование исходного кода с помощью `oxfmt`              |
| `bun run format:check` | Проверка соответствия форматированию `oxfmt`                 |

---

## 🛡 Pre-commit хук (Lefthook)

При выполнении `git commit` автоматически запускаются параллельные проверки:

1. **`typecheck`** — проверка типов через `vue-tsc --noEmit`
2. **`oxlint`** — моментальная проверка staged файлов через oxlint
3. **`oxfmt`** — форматирование staged файлов с авто-добавлением изменений (`stage_fixed: true`)

Все проверки отрабатывают суммарно менее чем за 1 секунду.

Для ручной проверки хуков выполните:

```bash
bun x lefthook run pre-commit
```
