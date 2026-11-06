<script setup lang="ts">
withDefaults(
  defineProps<{
    variant?: 'primary' | 'secondary' | 'outline'
  }>(),
  {
    variant: 'primary',
  },
)
</script>

<template>
  <button
    type="button"
    class="inline-flex items-center justify-center rounded-lg px-4 py-2 text-sm font-semibold transition active:scale-95 disabled:pointer-events-none disabled:opacity-50"
    :class="{
      'bg-emerald-500 text-slate-950 hover:bg-emerald-400': variant === 'primary',
      'bg-slate-800 text-slate-200 hover:bg-slate-700': variant === 'secondary',
      'border border-slate-700 text-slate-300 hover:bg-slate-800': variant === 'outline',
    }"
  >
    <slot />
  </button>
</template>
