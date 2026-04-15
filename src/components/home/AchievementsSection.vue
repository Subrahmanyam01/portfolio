<script setup lang="ts">
const hackathons = [
  {
    title: 'HackNIT 3.0 & SRM 3.0',
    issuer: 'Multiple Issuers',
    award: 'Overall Winner',
    date: '2022-2023',
    tags: ['Innovation', 'Technical Execution'],
    description:
      'Ranked top team for technical execution and innovation across back-to-back national hackathons.',
  },
  {
    title: 'Ingenious Hackathon',
    issuer: 'Ahmedabad University',
    award: 'Business Category Winner',
    date: '2023',
    tags: ['Product Strategy', 'Clean Code'],
    description:
      'Recognized for best product strategy and technical feasibility in the distributed systems track.',
  },
]

const publications = [
  {
    title: 'A Comprehensive Analysis of Real-World Image Captioning and Scene Identification',
    publisher: 'Cornell Archive (arXiv)',
    date: 'Aug 5, 2023',
    description:
      'Evaluates model performance in complex, poor-quality environments using a newly created dataset of 800+ images across 65 scene classes. Utilizes the IC3 approach to generate descriptive captions.',
    link: 'https://arxiv.org/abs/2308.02833',
    metrics: ['800+ Images', '65 Classes', 'IC3 Approach'],
  },
  {
    title: 'An Analysis of House Price Prediction Using Ensemble Learning Algorithms',
    publisher: 'Universal Wiser',
    date: 'May 29, 2023',
    description:
      'Predicts house prices by resolving data overfitting and inaccuracy issues found in previous models. Implements advanced ensemble algorithms.',
    link: 'https://ojs.wiserpub.com/index.php/RRCS/article/view/2639',
    metrics: ['XGBoost', 'Random Forest', 'SVM', 'AdaBoost'],
  },
]

const focusAreas = [
  'Distributed Systems',
  'Computer Vision',
  'Cloud Infrastructure',
  'Generative AI',
  'Predictive Modeling',
  'Real-time Data Processing',
  'MLOps',
  'System Architecture',
]
</script>

<template>
  <section
    id="achievements"
    class="relative min-h-screen bg-black py-24 lg:py-32 overflow-hidden border-b border-neutral-900"
  >
    <!-- Background Ambient Glow & Grid -->
    <div class="absolute inset-0 z-0 pointer-events-none">
      <div
        class="absolute inset-0 bg-[linear-gradient(to_right,#80808008_1px,transparent_1px),linear-gradient(to_bottom,#80808008_1px,transparent_1px)] bg-[size:40px_40px]"
      ></div>
      <div
        class="absolute top-1/4 right-0 w-[50vw] h-[50vw] bg-amber-500/5 rounded-full blur-[150px]"
      ></div>
      <div
        class="absolute bottom-0 left-0 w-[40vw] h-[30vw] bg-amber-500/5 rounded-full blur-[120px]"
      ></div>
    </div>

    <div class="max-w-[1440px] mx-auto px-6 lg:px-16 relative z-10 reveal-on-scroll">
      <!-- Section Header -->
      <div class="mb-16 lg:mb-24">
        <h2 class="text-xs uppercase tracking-[0.6em] text-amber-500 mb-4 font-bold font-mono">
          Recognition
        </h2>
        <div class="flex flex-col lg:flex-row lg:items-end lg:justify-between gap-6">
          <h1 class="text-5xl md:text-7xl xl:text-8xl font-black tracking-tighter italic text-white leading-none">
            AWARDS & <br /><span class="text-neutral-700">PUBLICATIONS</span>
          </h1>
          <p class="text-gray-400 text-base lg:text-lg leading-relaxed font-light max-w-md lg:text-right">
            A record of proven technical excellence across competitive hackathons and published academic research.
          </p>
        </div>
        <div class="w-24 h-0.5 bg-gradient-to-r from-amber-500 to-transparent mt-10"></div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 lg:gap-24">
        <!-- Hackathons Column -->
        <div class="flex flex-col">
          <h3 class="text-2xl lg:text-3xl font-black italic uppercase tracking-tighter text-white mb-8 flex items-center gap-4">
            <span class="text-amber-500 text-3xl font-light">01.</span> Competitive Hackathons
          </h3>

          <div class="space-y-6 lg:space-y-8 flex-grow">
            <div
              v-for="(hack, i) in hackathons"
              :key="i"
              class="group relative bg-neutral-950/60 border border-neutral-800 p-8 rounded-2xl hover:border-amber-500/40 transition-all duration-500 hover:shadow-[0_0_40px_rgba(251,191,36,0.06)] overflow-hidden"
            >
              <!-- Hover Ambient Internal -->
              <div class="absolute inset-0 bg-gradient-to-br from-amber-500/5 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-700 pointer-events-none"></div>

              <div class="relative z-10">
                <div class="flex flex-col sm:flex-row justify-between items-start gap-4 mb-6">
                  <div>
                    <div class="flex items-center gap-3 mb-2">
                      <div class="w-2 h-2 bg-amber-500 rounded-full animate-pulse shadow-[0_0_8px_rgba(251,191,36,0.6)]"></div>
                      <p class="text-amber-500 font-mono text-[10px] uppercase font-bold tracking-widest leading-none">
                        {{ hack.issuer }}
                      </p>
                    </div>
                    <h4 class="text-2xl font-black text-white italic tracking-tight group-hover:text-amber-400 transition-colors">
                      {{ hack.title }}
                    </h4>
                  </div>
                  <div class="flex flex-col items-end">
                    <span class="text-neutral-500 font-mono text-[10px] uppercase tracking-widest border border-neutral-800 bg-neutral-900 rounded-full px-3 py-1">
                      {{ hack.date }}
                    </span>
                  </div>
                </div>

                <div class="inline-block mb-4 px-3 py-1 bg-amber-500/10 border border-amber-500/30 rounded-md">
                  <span class="text-[10px] font-mono font-bold text-amber-500 tracking-widest uppercase">
                    🏆 {{ hack.award }}
                  </span>
                </div>

                <p class="text-gray-400 text-sm leading-relaxed mb-6 font-light">
                  {{ hack.description }}
                </p>

                <div class="flex flex-wrap gap-2 pt-4 border-t border-neutral-800/50">
                  <span
                    v-for="tag in hack.tags"
                    :key="tag"
                    class="text-[9px] font-mono px-2.5 py-1 bg-black border border-neutral-800 rounded uppercase tracking-wider text-neutral-400 group-hover:border-neutral-600 group-hover:text-neutral-300 transition-colors"
                  >
                    #{{ tag }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Publications Column -->
        <div class="flex flex-col">
          <h3 class="text-2xl lg:text-3xl font-black italic uppercase tracking-tighter text-white mb-8 flex items-center gap-4">
            <span class="text-amber-500 text-3xl font-light">02.</span> Academic Research
          </h3>

          <div class="space-y-6 lg:space-y-8 flex-grow">
            <div
              v-for="(pub, j) in publications"
              :key="j"
              class="group relative bg-neutral-950/60 border border-neutral-800 p-8 rounded-2xl hover:border-amber-500/40 transition-all duration-500 hover:shadow-[0_0_40px_rgba(251,191,36,0.06)] overflow-hidden flex flex-col justify-between"
            >
              <!-- Hover Ambient Internal -->
              <div class="absolute inset-0 bg-gradient-to-br from-amber-500/5 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-700 pointer-events-none"></div>
              
              <div class="relative z-10 flex-grow flex flex-col">
                <div class="flex justify-between items-start mb-4">
                  <p class="text-[10px] font-mono text-neutral-500 uppercase font-bold tracking-widest">
                    {{ pub.publisher }}
                  </p>
                  <p class="text-[10px] font-mono text-neutral-600">{{ pub.date }}</p>
                </div>

                <h4 class="text-xl font-bold text-white group-hover:text-amber-300 transition-colors leading-snug mb-4">
                  {{ pub.title }}
                </h4>

                <p class="text-sm text-gray-400 leading-relaxed font-light mb-6 flex-grow">
                  {{ pub.description }}
                </p>

                <div class="flex flex-wrap gap-2 mb-6">
                  <span
                    v-for="metric in pub.metrics"
                    :key="metric"
                    class="text-[9px] font-mono px-2 py-0.5 border border-cyan-500/20 bg-cyan-500/5 text-cyan-400 rounded-full"
                  >
                    {{ metric }}
                  </span>
                </div>
                
                <div class="pt-4 border-t border-neutral-800/50 mt-auto">
                  <a
                    :href="pub.link"
                    target="_blank"
                    class="inline-flex items-center gap-2 text-amber-500 text-[10px] font-black uppercase tracking-widest hover:text-amber-400 transition-colors group/link"
                  >
                    Read Publication
                    <svg class="w-3 h-3 transform group-hover/link:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
                    </svg>
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Research Focus Area Marquee or Grid -->
      <div class="mt-24 py-8 border-y border-neutral-900 bg-neutral-950/30">
        <div class="flex flex-col lg:flex-row lg:items-center gap-6 lg:gap-12 px-6 lg:px-8">
          <h4 class="text-[10px] font-mono text-neutral-500 uppercase tracking-[0.3em] font-bold shrink-0">
            Core Focus Areas //
          </h4>
          <div class="flex flex-wrap gap-3">
            <span
              v-for="focus in focusAreas"
              :key="focus"
              class="px-3 py-1.5 bg-neutral-900/80 border border-neutral-800 rounded font-mono text-[9px] text-gray-500 hover:text-amber-400 hover:border-amber-500/30 transition-colors cursor-default uppercase tracking-widest"
            >
              {{ focus }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Any additional specific styles */
</style>
