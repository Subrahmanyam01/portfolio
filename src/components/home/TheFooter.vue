<template>
  <footer class="relative bg-black border-t border-neutral-900 overflow-hidden">
    <!-- Subtle top glow -->
    <div class="absolute top-0 left-1/2 -translate-x-1/2 w-[60vw] h-px bg-gradient-to-r from-transparent via-amber-500/30 to-transparent pointer-events-none"></div>

    <div class="max-w-[1440px] mx-auto px-6 lg:px-16 py-10">
      <div class="flex flex-col md:flex-row justify-between items-center gap-8 md:gap-0">

        <!-- Left: Logo + Status -->
        <div class="flex items-center gap-4">
          <div class="w-8 h-8 bg-amber-500 rounded-sm flex items-center justify-center font-black text-black text-xs">
            SK
          </div>
          <div>
            <div class="flex items-center gap-2">
              <div class="w-1.5 h-1.5 rounded-full bg-green-400 animate-pulse shadow-[0_0_6px_rgba(74,222,128,0.7)]"></div>
              <span class="text-[9px] font-mono text-green-400/70 uppercase tracking-widest">Node_Status: Online</span>
            </div>
            <p class="text-xs font-mono text-neutral-600 mt-0.5">
              root@skonakanchi:~$ <span class="animate-pulse text-amber-500/60">_</span>
            </p>
          </div>
        </div>

        <!-- Center: Nav links -->
        <div class="flex gap-6 lg:gap-10">
          <a
            href="https://linkedin.com/in/subrahmanyam-konakanchi-91ba651bb/"
            target="_blank"
            class="text-[10px] font-mono uppercase tracking-widest text-neutral-600 hover:text-amber-500 transition-colors duration-300"
          >
            [ LinkedIn ]
          </a>
          <a
            href="https://github.com/Subrahmanyam01"
            target="_blank"
            class="text-[10px] font-mono uppercase tracking-widest text-neutral-600 hover:text-amber-500 transition-colors duration-300"
          >
            [ GitHub ]
          </a>
          <a
            href="mailto:lc.subrahmanyam@gmail.com"
            class="text-[10px] font-mono uppercase tracking-widest text-neutral-600 hover:text-amber-500 transition-colors duration-300"
          >
            [ Email ]
          </a>
        </div>

        <!-- Right: Build info -->
        <div class="text-right">
          <p class="text-[9px] font-mono text-neutral-700 uppercase tracking-widest leading-relaxed">
            Deployment_v2.0.26 // Built with Vue 3 + Tailwind<br />
            Delray Beach, Florida, USA · 2026
          </p>
        </div>

      </div>
    </div>
  </footer>
</template>
