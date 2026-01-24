<script setup>
const navItems = ['Home', 'About', 'Education', 'Experience', 'Projects', 'Skills']
</script>

<style scoped>
/* Ensure the body has padding-top so content doesn't hide under the fixed nav */
nav {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}
</style>

<template>
  <nav
    class="fixed top-0 left-0 w-full z-50 bg-black/60 backdrop-blur-xl border-b border-neutral-900"
  >
    <div class="max-w-7xl mx-auto h-20 flex flex-row items-center justify-between px-6 lg:px-12">
      <div class="flex items-center gap-3 group cursor-pointer">
        <div
          class="w-8 h-8 bg-amber-500 rounded-sm flex items-center justify-center font-black text-black text-xs group-hover:rotate-90 transition-transform duration-500"
        >
          SK
        </div>
        <div class="hidden md:block">
          <p
            class="text-[10px] font-mono text-amber-500 font-bold leading-none uppercase tracking-widest"
          >
            Architect
          </p>
          <p class="text-[10px] font-mono text-neutral-500 leading-none uppercase">v2.0.26</p>
        </div>
      </div>

      <div class="flex flex-row items-center gap-6 lg:gap-10">
        <div v-for="item in navItems" :key="item" class="relative group cursor-pointer">
          <span
            class="text-[11px] lg:text-xs font-mono font-bold uppercase tracking-[0.2em] text-neutral-400 group-hover:text-amber-500 transition-colors duration-300"
          >
            {{ item }}
          </span>

          <div
            class="absolute -bottom-1 left-0 w-0 h-[2px] bg-amber-500 group-hover:w-full transition-all duration-500 ease-out"
          ></div>

          <div
            class="absolute -top-4 left-1/2 -translate-x-1/2 w-1 h-1 bg-amber-500 rounded-full opacity-0 group-hover:opacity-100 group-hover:animate-pulse transition-opacity"
          ></div>
        </div>

        <button
          class="ml-4 px-5 py-2 border border-amber-500/50 text-amber-500 font-mono text-[10px] uppercase tracking-widest hover:bg-amber-500 hover:text-black transition-all duration-300 hidden sm:block"
        >
          Connect_
        </button>
      </div>
    </div>
  </nav>
</template>

<style></style>
