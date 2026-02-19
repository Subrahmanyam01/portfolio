<script setup lang="ts">
import gatorsLogo from '@/assets/florida_gators.jpg'
import srm from '@/assets/srm.jpg'

const educationHistory = [
  {
    university: 'University of Florida',
    location: 'Gainesville, FL',
    period: 'Aug 2023 - May 2025',
    degree: 'MS in Computer and Information Science Engineering',
    cgpa: '3.90 / 4.00',
    image: gatorsLogo,
  },
  {
    university: 'SRM University',
    location: 'Amaravati, AP',
    period: 'June 2019 - May 2023',
    degree: 'Bachelors in Computer Science Engineering',
    cgpa: '3.81 / 4.00',
    image: srm,
  },
]
</script>

<template>
  <section
    id="education"
    class="min-h-screen bg-black flex items-center justify-center border-t border-neutral-900 bg-dot-matrix relative overflow-hidden py-32"
  >
    <div class="max-w-7xl mx-auto px-6 lg:px-24 w-full">
      <div class="flex flex-col lg:flex-row gap-16 lg:gap-24">
        <!-- Left: Title Sticky -->
        <div class="lg:w-1/3">
          <div class="sticky top-32">
            <h2
              class="text-amber-500 font-mono tracking-[0.4em] uppercase text-[10px] mb-4 font-bold"
            >
              Learning Path
            </h2>
            <h1
              class="text-4xl md:text-6xl font-black italic uppercase tracking-tighter text-white mb-8"
            >
              Edu<br /><span class="text-neutral-700">cation</span>
            </h1>
            <div class="w-16 h-1 bg-amber-500 rounded-full mb-8"></div>
            <p class="text-gray-400 text-sm leading-relaxed">
              Building a strong theoretical foundation in distributed systems and software
              engineering.
            </p>
          </div>
        </div>

        <!-- Right: Timeline & Cards -->
        <div class="lg:w-2/3 relative">
          <!-- Vertical Line -->
          <div class="absolute left-[19px] top-4 bottom-0 w-[2px] bg-neutral-800"></div>

          <div class="flex flex-col gap-12">
            <div v-for="(edu, index) in educationHistory" :key="index" class="relative pl-12 group">
              <!-- Timeline Dot -->
              <div
                class="absolute left-0 top-6 w-10 h-10 -ml-[0.5px] z-10 flex items-center justify-center transition-all duration-300 scale-100 group-hover:scale-110"
              >
                <div
                  class="w-3 h-3 rounded-full bg-black border-2 border-neutral-600 group-hover:border-amber-500 bg-neutral-900 group-hover:bg-amber-500/20 transition-colors duration-300"
                ></div>
              </div>

              <!-- Card -->
              <div
                class="bg-neutral-900/30 border border-neutral-800 rounded-2xl overflow-hidden hover:border-amber-500/30 transition-all duration-300 group-hover:bg-neutral-900/50 group-hover:shadow-[0_0_30px_rgba(0,0,0,0.3)]"
              >
                <div class="p-6 md:p-8 flex flex-col gap-6">
                  <div class="flex items-start justify-between gap-4">
                    <div class="flex gap-4 items-center">
                      <div class="w-12 h-12 rounded-full overflow-hidden border border-neutral-700">
                        <img :src="edu.image" class="w-full h-full object-cover" />
                      </div>
                      <div>
                        <h2
                          class="text-xl font-bold text-white uppercase tracking-tight group-hover:text-amber-400 transition-colors"
                        >
                          {{ edu.university }}
                        </h2>
                        <p class="text-sm font-medium text-neutral-500">{{ edu.location }}</p>
                      </div>
                    </div>
                    <div
                      class="text-xs font-mono text-neutral-500 bg-black/30 px-3 py-1.5 rounded border border-neutral-800 whitespace-nowrap self-start"
                    >
                      {{ edu.period }}
                    </div>
                  </div>

                  <div class="border-t border-neutral-800 pt-6">
                    <h4
                      class="text-[10px] font-mono text-amber-500/70 uppercase tracking-widest mb-2 font-bold"
                    >
                      Degree
                    </h4>
                    <p class="text-lg text-white font-medium mb-4 leading-tight">
                      {{ edu.degree }}
                    </p>
                    <div class="flex items-center gap-2">
                      <span class="text-neutral-500 text-xs italic">CGPA:</span>
                      <span class="text-amber-500 font-bold font-mono">{{ edu.cgpa }}</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.bg-dot-matrix {
  background-image: radial-gradient(rgba(251, 191, 36, 0.08) 1px, transparent 1px);
  background-size: 20px 20px;
}
</style>
