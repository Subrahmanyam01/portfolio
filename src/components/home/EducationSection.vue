<script setup lang="ts">
import gatorsLogo from '@/assets/florida_gators.jpg'
import srm from '@/assets/srm.jpg'

const educationHistory = [
  {
    university: 'University of Florida',
    location: 'Gainesville, FL',
    period: 'Aug 2023 - May 2025',
    degree: 'MS in Computer Science',
    cgpa: '3.90 / 4.00',
    image: gatorsLogo,
    details: 'Specialization in Distributed Systems and Applied AI/ML.',
  },
  {
    university: 'SRM University',
    location: 'Amaravati, India',
    period: 'June 2019 - May 2023',
    degree: 'BS in Computer Science',
    cgpa: '3.81 / 4.00',
    image: srm,
    details: 'Core focus on Algorithms, Data Structures, and Software Engineering.',
  },
]

const certifications = [
  { name: 'AWS Certified Developer Associate', issuer: 'Amazon Web Services' },
  { name: 'Google Generative AI Leader', issuer: 'Google Cloud' },
]
</script>

<template>
  <section
    id="education"
    class="min-h-screen bg-black border-t border-neutral-900 py-32 relative overflow-hidden flex items-center justify-center text-center"
  >
    <!-- Background Elements -->
    <div class="absolute inset-0 z-0">
      <div
        class="absolute inset-0 bg-[linear-gradient(to_right,#80808012_1px,transparent_1px),linear-gradient(to_bottom,#80808012_1px,transparent_1px)] bg-[size:40px_40px]"
      ></div>
      <div
        class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[60vw] h-[60vw] bg-amber-500/5 rounded-full blur-[120px] pointer-events-none"
      ></div>
    </div>

    <!-- Main Content Container -->
    <div
      class="max-w-[1600px] mx-auto px-6 lg:px-24 z-10 reveal-on-scroll w-full flex flex-col items-center"
    >
      <!-- Section Header -->
      <div class="mb-16 lg:mb-24 flex flex-col items-center">
        <h2 class="text-amber-500 font-mono tracking-[0.4em] uppercase text-xs mb-4 font-bold">
          Academic Foundation
        </h2>
        <h1
          class="text-5xl lg:text-7xl xl:text-8xl font-black italic uppercase tracking-tighter text-white leading-none"
        >
          Edu<span class="text-neutral-700">cation</span>
        </h1>
        <div class="w-20 lg:w-32 h-1 bg-amber-500 rounded-full mt-8"></div>
      </div>

      <!-- Education Cards Stack -->
      <div class="w-full max-w-4xl flex flex-col gap-6 lg:gap-10">
        <div
          v-for="(edu, index) in educationHistory"
          :key="index"
          class="group relative w-full text-left"
        >
          <div
            class="relative bg-neutral-950/40 border border-neutral-800 rounded-3xl overflow-hidden hover:border-amber-500/30 transition-all duration-500 p-8 lg:p-12 shadow-[0_0_50px_rgba(0,0,0,0.5)] flex flex-col md:flex-row gap-8 lg:gap-12 items-center md:items-start"
          >
            <!-- Logo Section -->
            <div
              class="w-20 h-20 lg:w-24 lg:h-24 rounded-2xl overflow-hidden border border-neutral-800 flex-shrink-0 bg-neutral-900 group-hover:scale-110 transition-transform duration-700"
            >
              <img
                :src="edu.image"
                class="w-full h-full object-cover opacity-80 group-hover:opacity-100 transition-opacity"
                :alt="edu.university"
              />
            </div>

            <!-- Content Section -->
            <div class="flex-grow flex flex-col gap-6 w-full">
              <div class="flex flex-col md:flex-row md:items-center justify-between gap-4">
                <div class="text-center md:text-left">
                  <h2
                    class="text-2xl lg:text-3xl font-bold text-white tracking-tight group-hover:text-amber-500 transition-colors"
                  >
                    {{ edu.university }}
                  </h2>
                  <p
                    class="text-neutral-500 font-medium uppercase tracking-[0.2em] text-[10px] mt-1 italic"
                  >
                    {{ edu.location }}
                  </p>
                </div>
                <div
                  class="text-[10px] font-mono text-neutral-500 bg-neutral-900/80 px-4 py-2 rounded-full border border-neutral-800 whitespace-nowrap self-center md:self-start uppercase tracking-wider"
                >
                  {{ edu.period }}
                </div>
              </div>

              <div
                class="flex flex-col md:flex-row justify-between items-end gap-6 pt-6 border-t border-neutral-900"
              >
                <div class="w-full text-center md:text-left space-y-2">
                  <h4
                    class="text-[10px] font-mono text-amber-500/70 uppercase tracking-[0.3em] mb-2 font-bold"
                  >
                    Degree // Specialization
                  </h4>
                  <p class="text-lg lg:text-xl text-neutral-300 font-medium leading-snug">
                    {{ edu.degree }}
                  </p>
                  <p class="text-sm text-neutral-500 font-light">
                    {{ edu.details }}
                  </p>
                </div>

                <div class="flex-shrink-0 text-center md:text-right w-full md:w-auto">
                  <p class="text-[9px] font-mono text-neutral-700 uppercase tracking-widest mb-1">
                    Academic_GPA
                  </p>
                  <p
                    class="text-3xl lg:text-4xl font-black text-amber-500/90 font-mono tracking-tighter leading-none"
                  >
                    {{ edu.cgpa.split(' / ')[0]
                    }}<span class="text-neutral-800 text-lg">/{{ edu.cgpa.split(' / ')[1] }}</span>
                  </p>
                </div>
              </div>
            </div>

            <!-- Decorative glow -->
            <div
              class="absolute -top-12 -right-12 w-48 h-48 bg-amber-500/5 blur-[80px] opacity-0 group-hover:opacity-100 transition-opacity pointer-events-none"
            ></div>
          </div>
        </div>
      </div>

      <!-- Certifications Section -->
      <div class="mt-24 w-full max-w-4xl text-left">
        <div class="flex items-center gap-4 mb-10">
          <div class="h-px flex-grow bg-neutral-900"></div>
          <h3 class="text-xs font-mono text-neutral-600 uppercase tracking-[0.5em]">
            Verified_Certs
          </h3>
          <div class="h-px flex-grow bg-neutral-900"></div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div
            v-for="cert in certifications"
            :key="cert.name"
            class="group bg-neutral-950/50 border border-neutral-900 rounded-2xl p-6 flex items-center justify-between hover:border-amber-500/20 transition-all duration-300"
          >
            <div>
              <p class="text-[9px] font-mono text-amber-500/50 uppercase tracking-widest mb-1.5">
                {{ cert.issuer }}
              </p>
              <p class="text-sm font-bold text-white uppercase tracking-tight group-hover:text-amber-500 transition-colors">
                {{ cert.name }}
              </p>
            </div>
            <div class="w-8 h-8 rounded-lg bg-neutral-900 border border-neutral-800 flex items-center justify-center group-hover:border-amber-500/40 transition-all">
              <svg viewBox="0 0 24 24" class="w-4 h-4 text-amber-550/40 group-hover:text-amber-500" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M22 11.08V12a10 10 0 1 1-5.93-9.14" />
                <polyline points="22 4 12 14.01 9 11.01" />
              </svg>
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
