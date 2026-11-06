# Agent Guidelines & Engineering Standards

This document establishes critical operational instructions, architectural guidelines, and quality constraints for AI coding assistants working in this repository.

---

## 1. 🌐 Language Requirement (Strict)

- **English Only**: All codebase artifacts must be written strictly in **English**.
  - Source code, variable/function/type identifiers
  - Comments and documentation (JSDoc, TSDoc, Markdown)
  - Git commit messages, branch names, and pull requests
  - UI text and localization keys (unless a multi-language i18n module is explicitly requested)

---

## 2. 📦 Package Manager & Runtime

- **Package Manager**: Strictly use **Bun** (`bun`).
  - Do **NOT** use `npm`, `yarn`, or `pnpm`.
  - Do **NOT** generate or commit `package-lock.json`, `yarn.lock`, or `pnpm-lock.yaml`.
  - Adding dependencies: `bun add <pkg>` or `bun add -d <pkg>` (always prefer devDependencies when appropriate).
  - Lifecycle scripts: `lefthook` is trusted in `package.json` (`trustedDependencies: ["lefthook"]`).

---

## 3. 🛠 Quality & Formatting Tooling

- **Linter**: Use **`oxlint`** (`bun run lint`, `bun run lint:fix`).
  - Do **NOT** install or introduce legacy ESLint unless explicitly directed.
  - Oxlint configuration lives in `.oxlintrc.json`.
- **Formatter**: Use **`oxfmt`** (`bun run format`, `bun run format:check`).
  - Do **NOT** install Prettier.
  - Configuration is in `.oxfmtrc.json` (Tailwind CSS class sorting and import sorting are enabled).
- **Type Checker**: Use **`vue-tsc`** (`bun run typecheck`).
- **Git Hooks**: Managed by **`lefthook`** (`lefthook.yml`). Pre-commit automatically runs `oxlint`, `oxfmt`, and `typecheck` in parallel.

---

## 4. 🧩 Vue 3 & TypeScript Best Practices

- **SFC Syntax**: Always use Single File Components with `<script setup lang="ts">`. Avoid Options API.
- **Strict Typing**:
  - Never use `any`. Use strict union types, interfaces, generics, or `unknown` with type guards.
  - Define props with generic type arguments:
    ```vue
    <script setup lang="ts">
    interface Props {
      title: string
      disabled?: boolean
    }
    const props = withDefaults(defineProps<Props>(), {
      disabled: false,
    })
    </script>
    ```
  - Define emits with type-safe syntax:
    ```vue
    <script setup lang="ts">
    const emit = defineEmits<{
      (e: 'update', value: string): void
      (e: 'close'): void
    }>()
    </script>
    ```
- **File & Symbol Naming**:
  - Components: `PascalCase.vue` (e.g., `UserProfile.vue`, `NavigationMenu.vue`).
  - Composables: `useCamelCase.ts` (e.g., `useAuth.ts`, `useWindowSize.ts`) placed in `src/composables/`.
  - Stores: `camelCase.ts` or `name.ts` (e.g., `user.ts`, `settings.ts`) in `src/stores/`.
- **Path Aliases**: Always use `@/` alias for imports pointing into `src/` (e.g., `import { useUserStore } from '@/stores/user'`).

---

## 5. 🎨 Styling (Tailwind CSS v4)

- **Zero Config**: Tailwind CSS v4 is integrated via `@tailwindcss/vite` and `@import "tailwindcss";` in `src/assets/main.css`.
- Do **NOT** create legacy `tailwind.config.js` or `postcss.config.js`.
- Class sorting is handled automatically by `oxfmt`.

---

## 6. 🗄 State Management & Routing

- **Pinia**:
  - Use the Setup Store syntax (`defineStore('name', () => { ... })`).
  - Keep stores modular, focused on specific business domains.
- **Vue Router**:
  - Always use dynamic imports for views/pages (`component: () => import('@/views/...')`) for route-level code splitting.

---

## 7. ✅ Verification Checklist Before Submitting Changes

Before marking any task as complete, an agent must execute and ensure passing status:

1. `bun run typecheck` (zero TypeScript errors)
2. `bun run lint` (zero Oxlint warnings or errors)
3. `bun run format:check` (zero unformatted files; run `bun run format` if needed)
4. `bun run build` (production build completes with exit code 0)
5. If developing UI components or views, verify in browser and check console for runtime errors.
