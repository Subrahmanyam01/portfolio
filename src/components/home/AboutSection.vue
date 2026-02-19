<template>
  <section
    id="about"
    class="snap-start min-h-screen w-full bg-neutral-950 relative overflow-hidden flex items-center justify-center bg-terminal-lines"
  >
    <div
      class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] bg-amber-500/5 rounded-full blur-[120px] pointer-events-none"
    ></div>

    <div class="max-w-7xl mx-auto px-6 lg:px-24 w-full reveal-on-scroll relative z-10">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-20 items-center">
        <div class="lg:col-span-7 space-y-8 lg:space-y-10">
          <div class="space-y-2">
            <h2 class="text-amber-500 font-mono tracking-[0.4em] uppercase text-[10px] font-bold">
              Nice to meet you
            </h2>
            <h1
              class="text-5xl lg:text-7xl font-black italic uppercase tracking-tighter leading-tight text-white"
            >
              I build systems with <span class="text-neutral-700">soul.</span>
            </h1>
          </div>

          <div class="space-y-6 text-lg text-gray-300 leading-relaxed font-light">
            <p>
              I’m <span class="text-white font-medium">Subrahmanyam</span>—a curious builder and a
              Computer Engineering graduate from the University of Florida. To me, code isn't just
              lines of logic; it’s a tool for crafting
              <span class="text-amber-400/80 italic">meaningful experiences</span>.
            </p>

            <p>
              Whether I'm architecting a complex backend or refining a user interface, I focus on
              the "why" behind the "how." I’ve spent over six years bridging the gap between
              <span class="text-white font-medium italic">robust engineering</span> and
              <span class="text-white font-medium">human impact</span>, ensuring that every
              deployment is as maintainable as it is powerful.
            </p>

            <p>
              Beyond the screen, you’ll find me playing the
              <span class="text-amber-500 font-medium italic">flute</span>, hiking local trails, or
              geeking out over a new framework. I believe the best software comes from a blend of
              technical rigor and a creative spirit.
            </p>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-3 gap-6 pt-4">
            <div class="flex flex-col gap-2">
              <span class="text-amber-500 font-mono text-[10px] uppercase font-bold tracking-widest"
                >The Teacher</span
              >
              <p class="text-xs text-neutral-500">
                I get immense joy from teaching—from recursion to Docker.
              </p>
            </div>
            <div class="flex flex-col gap-2 border-l border-neutral-800 pl-6">
              <span class="text-amber-500 font-mono text-[10px] uppercase font-bold tracking-widest"
                >The Tinkerer</span
              >
              <p class="text-xs text-neutral-500">
                Always happy to automate away daily annoyances with code.
              </p>
            </div>
            <div class="flex flex-col gap-2 border-l border-neutral-800 pl-6">
              <span class="text-amber-500 font-mono text-[10px] uppercase font-bold tracking-widest"
                >The Listener</span
              >
              <p class="text-xs text-neutral-500">
                Always hunting for new music or a cool idea to collaborate on.
              </p>
            </div>
          </div>
        </div>

        <div class="lg:col-span-5 flex justify-center items-center">
          <div class="relative group">
            <div
              class="absolute -inset-4 border border-neutral-800 rounded-full animate-[spin_30s_linear_infinite] pointer-events-none"
            ></div>

            <div class="relative z-10 overflow-hidden rounded-2xl bg-neutral-900 shadow-2xl">
              <img
                src="@/assets/megreet.png"
                alt="Subrahmanyam Konakanchi"
                class="max-h-[500px] xl:max-h-[550px] w-auto object-contain transition-transform duration-700 group-hover:scale-105"
              />

              <div
                class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col justify-end p-8"
              >
                <p class="text-amber-500 font-mono text-[10px] uppercase mb-1">Status</p>
                <p class="text-sm font-bold italic uppercase text-white">
                  Lifelong Learner. Curious Builder.
                </p>
              </div>
            </div>

            <div
              class="absolute -bottom-6 -left-6 lg:bottom-10 lg:-left-20 bg-amber-500 p-6 rounded-lg rotate-[-3deg] shadow-xl hidden md:block"
            >
              <p class="text-black font-black text-xl leading-none italic uppercase">
                FLORIDA<br />BASED
              </p>
              <p
                class="text-black/60 font-mono text-[10px] mt-1 font-bold uppercase tracking-tighter"
              >
                U_Florida :: MS
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.bg-terminal-lines {
  background:
    linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%),
    linear-gradient(90deg, rgba(251, 191, 36, 0.02), rgba(251, 191, 36, 0.01));
  background-size:
    100% 4px,
    2px 100%;
}
</style>
