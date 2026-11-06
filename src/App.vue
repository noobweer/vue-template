<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="flex min-h-screen flex-col">
    <!-- Header -->
    <header class="sticky top-0 z-50 border-b border-slate-800 bg-slate-950/80 backdrop-blur-md">
      <div class="mx-auto flex h-16 max-w-5xl items-center justify-between px-4 sm:px-6">
        <RouterLink
          to="/"
          class="flex items-center gap-2.5 font-bold tracking-tight text-white transition hover:opacity-90"
        >
          <div
            class="flex h-8 w-8 items-center justify-center rounded-lg border border-emerald-500/30 bg-emerald-500/10 text-sm font-black text-emerald-400"
          >
            V
          </div>
          <span>Vue Template</span>
        </RouterLink>

        <nav class="flex items-center gap-1 sm:gap-2">
          <RouterLink
            to="/"
            class="rounded-lg px-3 py-1.5 text-sm font-medium text-slate-400 transition hover:bg-slate-900 hover:text-white"
            active-class="!text-emerald-400 !bg-slate-900"
          >
            Home
          </RouterLink>
          <RouterLink
            to="/about"
            class="rounded-lg px-3 py-1.5 text-sm font-medium text-slate-400 transition hover:bg-slate-900 hover:text-white"
            active-class="!text-emerald-400 !bg-slate-900"
          >
            About
          </RouterLink>
        </nav>
      </div>
    </header>

    <!-- Main Content -->
    <main class="mx-auto w-full max-w-5xl flex-1 px-4 py-10 sm:px-6">
      <RouterView />
    </main>

    <!-- Footer -->
    <footer class="border-t border-slate-800/80 py-6 text-center text-xs text-slate-500">
      <div class="mx-auto max-w-5xl px-4">
        Vue 3 SPA Template &bull; Built with Vite, TypeScript & Tailwind CSS v4
      </div>
    </footer>
  </div>
</template>
