<script setup lang="ts">
import BaseButton from '@/components/BaseButton.vue'
import { useCounterStore } from '@/stores/counter'

const counter = useCounterStore()

const stack = [
  { name: 'Vue 3.5', desc: 'Composition API, <script setup>', tag: 'Core' },
  { name: 'TypeScript', desc: 'Strict mode, vue-tsc verification', tag: 'Type Safety' },
  { name: 'Vite', desc: 'Lightning-fast HMR and bundling', tag: 'Build' },
  { name: 'Tailwind CSS v4', desc: 'Zero-config modern CSS styling', tag: 'Design' },
  { name: 'Pinia', desc: 'Type-safe reactive state management', tag: 'State' },
  { name: 'Vue Router', desc: 'SPA client-side routing', tag: 'Routing' },
  { name: 'oxlint', desc: 'Rust-powered ultra-fast linter', tag: 'Quality' },
  { name: 'oxfmt', desc: 'Rust-based code formatter with class sorting', tag: 'Format' },
  { name: 'Lefthook', desc: 'Blazing fast Git pre-commit hooks', tag: 'DevOps' },
]
</script>

<template>
  <div class="space-y-12">
    <!-- Hero Section -->
    <section class="space-y-4 text-center">
      <div
        class="inline-flex items-center gap-2 rounded-full border border-emerald-500/30 bg-emerald-500/10 px-3 py-1 text-xs font-medium text-emerald-400"
      >
        <span class="h-1.5 w-1.5 animate-pulse rounded-full bg-emerald-400"></span>
        Ready for Production SPA
      </div>
      <h1 class="text-4xl font-extrabold tracking-tight text-white sm:text-5xl">
        Clean
        <span class="bg-gradient-to-r from-emerald-400 to-teal-300 bg-clip-text text-transparent"
          >Vue 3</span
        >
        Starter Template
      </h1>
      <p class="mx-auto max-w-2xl text-base text-slate-400 sm:text-lg">
        Minimalist, high-performance frontend template powered by Vite, TypeScript, Tailwind v4,
        Oxlint, Oxfmt, and Lefthook.
      </p>
    </section>

    <!-- Interactive Counter Demo (Pinia Store) -->
    <section
      class="mx-auto max-w-md rounded-2xl border border-slate-800 bg-slate-900/60 p-6 shadow-xl backdrop-blur-sm"
    >
      <div class="flex items-center justify-between border-b border-slate-800 pb-4">
        <div>
          <h2 class="text-base font-semibold text-white">Pinia Store Example</h2>
          <p class="text-xs text-slate-400">State & computed reactivity</p>
        </div>
        <span class="rounded bg-slate-800 px-2 py-1 font-mono text-xs text-emerald-400"
          >stores/counter.ts</span
        >
      </div>

      <div class="my-6 text-center">
        <div class="text-5xl font-black tracking-tight text-white tabular-nums">
          {{ counter.count }}
        </div>
        <p class="mt-2 text-xs text-slate-400">
          Double value: <span class="font-mono text-emerald-400">{{ counter.doubleCount }}</span>
        </p>
      </div>

      <div class="grid grid-cols-3 gap-2">
        <BaseButton variant="secondary" @click="counter.decrement"> - 1 </BaseButton>
        <BaseButton variant="outline" @click="counter.reset"> Reset </BaseButton>
        <BaseButton variant="primary" @click="counter.increment"> + 1 </BaseButton>
      </div>
    </section>

    <!-- Stack Features Grid -->
    <section class="space-y-4">
      <h2 class="text-center text-xl font-bold text-white">Included Tooling & Libraries</h2>
      <div class="grid grid-cols-1 gap-4 sm:grid-cols-2 lg:grid-cols-3">
        <div
          v-for="item in stack"
          :key="item.name"
          class="rounded-xl border border-slate-800 bg-slate-900/40 p-4 transition hover:border-slate-700"
        >
          <div class="mb-2 flex items-center justify-between">
            <h3 class="font-semibold text-white">{{ item.name }}</h3>
            <span class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[11px] text-slate-400">{{
              item.tag
            }}</span>
          </div>
          <p class="text-sm text-slate-400">{{ item.desc }}</p>
        </div>
      </div>
    </section>
  </div>
</template>
