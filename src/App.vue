<script setup lang="ts">
const stack = [
  'Vue 3',
  'TypeScript',
  'Vite',
  'Tailwind CSS v4',
  'Vue DevTools',
  'Vue Router',
  'Pinia',
  'oxlint',
  'oxfmt',
  'Lefthook',
]

const commands = [
  { name: 'dev', cmd: 'bun run dev' },
  { name: 'build', cmd: 'bun run build' },
  { name: 'typecheck', cmd: 'bun run typecheck' },
  { name: 'lint', cmd: 'bun run lint' },
  { name: 'format', cmd: 'bun run format' },
]
</script>

<template>
  <main class="mx-auto max-w-lg p-8 font-sans">
    <h1 class="mb-6 text-xl font-bold">Vue Template</h1>

    <section class="mb-6">
      <h2 class="mb-2 text-xs font-semibold text-slate-400 uppercase">Стек</h2>
      <ul class="flex flex-wrap gap-1.5 text-xs">
        <li v-for="item in stack" :key="item" class="rounded bg-slate-800 px-2 py-1 text-slate-200">
          {{ item }}
        </li>
      </ul>
    </section>

    <section>
      <h2 class="mb-2 text-xs font-semibold text-slate-400 uppercase">Команды</h2>
      <dl class="space-y-1 font-mono text-xs">
        <div
          v-for="item in commands"
          :key="item.name"
          class="flex items-center justify-between border-b border-slate-800 py-1"
        >
          <dt class="text-slate-400">{{ item.name }}</dt>
          <dd class="text-emerald-400">{{ item.cmd }}</dd>
        </div>
      </dl>
    </section>
  </main>
</template>
