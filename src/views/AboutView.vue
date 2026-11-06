<script setup lang="ts">
const commands = [
  { cmd: 'bun run dev', desc: 'Start Vite local dev server' },
  { cmd: 'bun run build', desc: 'Typecheck and build for production' },
  { cmd: 'bun run typecheck', desc: 'Run vue-tsc type checking' },
  { cmd: 'bun run lint', desc: 'Run oxlint' },
  { cmd: 'bun run lint:fix', desc: 'Auto-fix issues with oxlint' },
  { cmd: 'bun run format', desc: 'Format all files with oxfmt' },
  { cmd: 'bun run format:check', desc: 'Verify formatting with oxfmt' },
]

const structure = [
  { path: 'src/assets/', desc: 'Global styles (Tailwind CSS v4 entry)' },
  { path: 'src/components/', desc: 'Reusable UI components' },
  { path: 'src/router/', desc: 'Vue Router SPA route definitions' },
  { path: 'src/stores/', desc: 'Pinia state management stores' },
  { path: 'src/views/', desc: 'Page-level route views' },
  { path: 'lefthook.yml', desc: 'Pre-commit hook running oxlint, oxfmt & typecheck' },
  { path: '.oxlintrc.json', desc: 'Oxlint configuration' },
  { path: '.oxfmtrc.json', desc: 'Oxfmt configuration (with Tailwind class sorting)' },
]
</script>

<template>
  <div class="mx-auto max-w-3xl space-y-8">
    <div class="space-y-2">
      <h1 class="text-3xl font-bold text-white">About Template</h1>
      <p class="text-slate-400">
        This template is engineered to provide an instant, clean, and unopinionated starting point
        for modern Vue SPA applications.
      </p>
    </div>

    <!-- Project Structure -->
    <div class="space-y-4 rounded-xl border border-slate-800 bg-slate-900/40 p-6">
      <h2 class="text-lg font-semibold text-white">Project Structure</h2>
      <div class="grid grid-cols-1 gap-2">
        <div
          v-for="item in structure"
          :key="item.path"
          class="flex flex-col justify-between gap-1 border-b border-slate-800/60 py-1.5 last:border-0 sm:flex-row sm:items-center"
        >
          <span class="font-mono text-xs text-emerald-400">{{ item.path }}</span>
          <span class="text-xs text-slate-400">{{ item.desc }}</span>
        </div>
      </div>
    </div>

    <!-- Commands Table -->
    <div class="space-y-4 rounded-xl border border-slate-800 bg-slate-900/40 p-6">
      <h2 class="text-lg font-semibold text-white">Available Scripts</h2>
      <div class="grid grid-cols-1 gap-2">
        <div
          v-for="item in commands"
          :key="item.cmd"
          class="flex flex-col justify-between gap-1 border-b border-slate-800/60 py-1.5 last:border-0 sm:flex-row sm:items-center"
        >
          <code class="rounded bg-slate-950 px-2 py-1 font-mono text-xs text-emerald-400">{{
            item.cmd
          }}</code>
          <span class="text-xs text-slate-400">{{ item.desc }}</span>
        </div>
      </div>
    </div>
  </div>
</template>
