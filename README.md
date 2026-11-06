# Vue 3 SPA Starter Template

A minimalist, high-performance starter template for Single Page Applications (SPA) built with **Vue 3**. Clean architecture, zero bloat, strict TypeScript, Rust-powered linting and formatting, and automated pre-commit verification.

---

## 🚀 Tech Stack

- **Vue 3.5+** (Composition API, `<script setup>`)
- **TypeScript** (Strict mode + `vue-tsc` build-time validation)
- **Vite** (Lightning-fast HMR and bundling)
- **Tailwind CSS v4** (`@tailwindcss/vite` zero-config integration)
- **Vue DevTools** (`vite-plugin-vue-devtools` in-app inspection)
- **Vue Router 5 & Pinia** (Ready-to-use SPA routing and reactive state management)
- **oxlint** (Rust-powered ultra-fast linter)
- **oxfmt** (Rust-powered formatter with built-in Tailwind CSS class and import sorting)
- **Lefthook** (Sub-second parallel Git pre-commit hooks)
- **Bun** (Fast package manager with automated lifecycle hook setup)

---

## 📁 Project Structure

```text
vue-template/
├── .vscode/                 # Recommended VS Code extensions (Volar, Oxc, Tailwind)
├── public/                  # Static assets (favicon.svg, etc.)
├── src/
│   ├── assets/              # Global styles (main.css importing Tailwind v4)
│   ├── components/          # Reusable UI components
│   ├── router/              # Vue Router SPA route definitions
│   ├── stores/              # Pinia state stores
│   ├── App.vue              # Minimal root component
│   └── main.ts              # Application entry point
├── AGENTS.md                # AI agent guidelines & engineering rules
├── env.d.ts                 # Vite environment type declarations
├── index.html               # SPA mounting entry
├── lefthook.yml             # Lefthook pre-commit configuration
├── .oxlintrc.json           # Oxlint configuration
├── .oxfmtrc.json            # Oxfmt configuration
├── tsconfig.json            # Root TypeScript configuration
├── tsconfig.app.json        # Application TypeScript configuration
├── tsconfig.node.json       # Tooling TypeScript configuration
├── vite.config.ts           # Vite configuration
└── package.json             # Scripts and dependencies
```

---

## 🛠 Available Scripts

| Script                 | Description                                                       |
| :--------------------- | :---------------------------------------------------------------- |
| `bun run dev`          | Start local Vite development server with Vue DevTools             |
| `bun run build`        | Validate types (`vue-tsc`) and bundle for production              |
| `bun run preview`      | Locally preview the production build                              |
| `bun run typecheck`    | Run TypeScript type checking without emitting files               |
| `bun run lint`         | Lint code using `oxlint`                                          |
| `bun run lint:fix`     | Automatically fix lint issues using `oxlint --fix`                |
| `bun run format`       | Format files using `oxfmt` (with Tailwind class & import sorting) |
| `bun run format:check` | Check code formatting compliance                                  |

---

## 🛡 Pre-commit Hooks (Lefthook)

Git hooks are automatically configured on `bun install`. Before any commit is created, Lefthook executes:

1. `typecheck` (`vue-tsc --noEmit`)
2. `oxlint` (staged files)
3. `oxfmt` (formats staged files and stages fixes automatically)
