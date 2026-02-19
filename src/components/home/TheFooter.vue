<template>
  <footer class="bg-black text-white p-12 border-t border-neutral-900 font-mono">
    <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-10">
      <div class="space-y-2">
        <div class="flex items-center gap-2">
          <div class="w-2 h-2 rounded-full bg-green-500 animate-pulse"></div>
          <p class="text-amber-500 text-[10px] uppercase tracking-widest font-bold">
            Node_Status: Online
          </p>
        </div>
        <p class="text-sm">root@skonakanchi:~$ <span class="animate-pulse">_</span></p>
      </div>

      <div class="flex gap-10">
        <a
          href="#"
          class="group text-xs uppercase tracking-widest text-neutral-400 hover:text-amber-500 transition-colors"
        >
          [ LinkedIn ]
        </a>
        <a
          href="#"
          class="group text-xs uppercase tracking-widest text-neutral-400 hover:text-amber-500 transition-colors"
        >
          [ GitHub ]
        </a>
        <a
          href="#"
          class="group text-xs uppercase tracking-widest text-neutral-400 hover:text-amber-500 transition-colors"
        >
          [ Email ]
        </a>
      </div>

      <div class="text-right">
        <p class="text-[9px] text-neutral-600 uppercase tracking-tighter">
          Deployment_v2.0.26 // Built with Vue 3 & Tailwind // Florida, USA
        </p>
      </div>
    </div>
  </footer>
</template>
