<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue'

const navItems = ['Home', 'About', 'Education', 'Experience', 'Projects', 'Achievements', 'Skills', 'Contact']
const activeSection = ref('home')

let observer: IntersectionObserver | null = null

onMounted(() => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          activeSection.value = entry.target.id
        }
      })
    },
    { threshold: 0.4 },
  )
  document.querySelectorAll('section[id]').forEach((el) => observer!.observe(el))
})

onBeforeUnmount(() => observer?.disconnect())
</script>

<template>
  <nav
    class="fixed top-0 left-0 w-full z-50 bg-black/60 backdrop-blur-xl border-b border-neutral-900"
  >
    <div class="max-w-[1600px] mx-auto h-20 flex flex-row items-center justify-between px-6 lg:px-12 xl:px-24">
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

      <div class="flex flex-row items-center gap-5 lg:gap-8">
        <a
          v-for="item in navItems"
          :key="item"
          :href="'#' + item.toLowerCase()"
          class="relative group cursor-pointer hidden lg:block"
        >
          <span
            class="text-[10px] font-mono font-bold uppercase tracking-[0.2em] transition-colors duration-300"
            :class="
              activeSection === item.toLowerCase()
                ? 'text-amber-500'
                : 'text-neutral-500 group-hover:text-amber-400'
            "
          >
            {{ item }}
          </span>
          <!-- Active underline -->
          <div
            class="absolute -bottom-1 left-0 h-[1.5px] bg-amber-500 transition-all duration-400 ease-out"
            :class="activeSection === item.toLowerCase() ? 'w-full' : 'w-0 group-hover:w-full'"
          ></div>
        </a>

        <a
          href="#contact"
          class="ml-4 px-5 py-2 border border-amber-500/50 text-amber-500 font-mono text-[10px] uppercase tracking-widest hover:bg-amber-500 hover:text-black transition-all duration-300 hidden sm:inline-block"
        >
          Connect_
        </a>
      </div>
    </div>
  </nav>
</template>

<style scoped>
nav {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}
</style>
