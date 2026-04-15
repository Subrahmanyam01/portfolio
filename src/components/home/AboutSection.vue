<script setup lang="ts">
const traits = [
  {
    code: '01',
    label: 'The Teacher',
    desc: 'I get immense joy from teaching — from recursion to Docker internals.',
  },
  {
    code: '02',
    label: 'The Tinkerer',
    desc: 'Always happy to automate away daily annoyances with code.',
  },
  {
    code: '03',
    label: 'The Listener',
    desc: 'Always hunting for new music or a cool idea to collaborate on.',
  },
]

const quickFacts = [
  { label: 'Location', value: 'Nashville, TN' },
  { label: 'Education', value: 'UF MS, SRM BS' },
  { label: 'Focus', value: 'Distributed Systems + AI' },
  { label: 'Experience', value: '4+ Years' },
]
</script>

<template>
  <section
    id="about"
    class="relative min-h-screen bg-black py-24 lg:py-32 overflow-hidden border-b border-neutral-900 flex items-center"
  >
    <!-- Background -->
    <div class="absolute inset-0 z-0 pointer-events-none">
      <div
        class="absolute inset-0 bg-[linear-gradient(to_right,#80808008_1px,transparent_1px),linear-gradient(to_bottom,#80808008_1px,transparent_1px)] bg-[size:40px_40px]"
      ></div>
      <div
        class="absolute top-1/2 left-0 -translate-y-1/2 w-[50vw] h-[50vw] bg-amber-500/5 rounded-full blur-[140px]"
      ></div>
    </div>

    <div class="max-w-[1440px] mx-auto px-6 lg:px-16 w-full relative z-10 reveal-on-scroll">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-16 lg:gap-20 items-center">
        <!-- Left: Text Content -->
        <div class="lg:col-span-7 space-y-10">
          <!-- Header -->
          <div>
            <h2 class="text-xs uppercase tracking-[0.6em] text-amber-500 mb-4 font-bold font-mono">
              Nice to meet you
            </h2>
            <h1
              class="text-5xl md:text-6xl xl:text-7xl font-black italic uppercase tracking-tighter leading-none text-white"
            >
              Engineering<br /><span class="text-neutral-700">with precision.</span>
            </h1>
            <div class="w-24 h-0.5 bg-gradient-to-r from-amber-500 to-transparent mt-8"></div>
          </div>

          <!-- Body Copy -->
          <div
            class="space-y-5 text-gray-400 text-base lg:text-lg leading-relaxed font-light max-w-2xl"
          >
            <p>
              I'm <span class="text-white font-semibold">Subrahmanyam</span> — a Software Engineer
              specializing in distributed systems and applied AI/ML solutions. With 
              <span class="text-amber-400 italic">over 4 years of experience</span> and an MS from the
              <span class="text-amber-400 italic">University of Florida</span>, I build 
              high-performance systems that bridge technical complexity and human impact.
            </p>
            <p>
              I was an early engineer at a <span class="text-white font-medium">YC W22 computer vision startup</span>, 
              where I delivered real-time inference pipelines across large-scale cloud infrastructure. 
              Currently, I'm building end-to-end platforms at <span class="text-white font-medium">Scholarship Auditions</span>, 
              integrating robust web systems with AI-driven automation.
            </p>
            <p>
              Whether I'm optimizing AWS cloud spend or architecting fault-tolerant async ingestion, 
              I focus on creating <span class="text-white italic">scalable, soul-driven technology</span> 
              that makes life meaningfully better.
            </p>
          </div>

          <!-- Quick Facts Row -->
          <div class="grid grid-cols-2 md:grid-cols-4 gap-3">
            <div
              v-for="fact in quickFacts"
              :key="fact.label"
              class="bg-neutral-950/60 border border-neutral-800 rounded-xl p-4 hover:border-amber-500/30 transition-colors duration-400"
            >
              <p class="text-[9px] font-mono text-neutral-600 uppercase tracking-widest mb-1.5">
                {{ fact.label }}
              </p>
              <p class="text-sm font-bold text-white leading-tight">{{ fact.value }}</p>
            </div>
          </div>

          <!-- Traits -->
          <div class="flex flex-col gap-0 divide-y divide-neutral-900">
            <div
              v-for="trait in traits"
              :key="trait.code"
              class="group flex items-start gap-5 py-5 hover:pl-2 transition-all duration-300"
            >
              <span class="text-[10px] font-mono text-amber-500/50 pt-0.5 shrink-0">{{
                trait.code
              }}</span>
              <div>
                <p
                  class="text-white font-bold text-sm mb-1 group-hover:text-amber-400 transition-colors"
                >
                  {{ trait.label }}
                </p>
                <p class="text-neutral-500 text-xs leading-relaxed">{{ trait.desc }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Right: Image Card -->
        <div class="lg:col-span-5 flex justify-center items-center">
          <div class="relative group w-full max-w-sm">
            <!-- Orbiting ring -->
            <div
              class="absolute -inset-6 border border-amber-500/10 rounded-3xl animate-spin-ultra pointer-events-none"
            ></div>
            <div
              class="absolute -inset-12 border border-amber-500/5 rounded-3xl animate-spin-ultra-reverse pointer-events-none"
            ></div>

            <!-- Photo card -->
            <div
              class="relative z-10 overflow-hidden rounded-2xl bg-neutral-900 border border-neutral-800 group-hover:border-amber-500/30 transition-colors duration-700 shadow-2xl"
            >
              <img
                src="@/assets/megreet.png"
                alt="Subrahmanyam Konakanchi"
                class="w-full object-cover transition-transform duration-700 group-hover:scale-105"
              />
              <!-- Overlay on hover -->
              <div
                class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col justify-end p-6"
              >
                <p class="text-amber-500 font-mono text-[9px] uppercase tracking-widest mb-1">
                  Status
                </p>
                <p class="text-sm font-bold italic uppercase text-white">
                  Curious Builder. MS CS (GPA 3.9).
                </p>
              </div>
            </div>

            <!-- Floating label -->
            <div
              class="absolute -bottom-5 -left-5 lg:-left-10 bg-amber-500 px-5 py-4 rounded-xl rotate-[-2deg] shadow-xl z-20"
            >
              <p class="text-black font-black text-base leading-none italic uppercase">
                Nashville<br />Based
              </p>
              <p class="text-black/60 font-mono text-[9px] mt-1 uppercase tracking-tight">
                U_Florida :: MS CS
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@keyframes spin-ultra {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
@keyframes spin-ultra-reverse {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(-360deg);
  }
}
.animate-spin-ultra {
  animation: spin-ultra 40s linear infinite;
}
.animate-spin-ultra-reverse {
  animation: spin-ultra-reverse 60s linear infinite;
}
</style>
