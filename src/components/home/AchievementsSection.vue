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
      'Recognized for best product strategy and technical feasibility in distributed systems track.',
  },
]

const publications = [
  {
    title: 'A Comprehensive Analysis of Real-World Image Captioning and Scene Identification',
    publisher: 'Cornell Archive',
    date: 'Aug 5, 2023',
    description:
      'Evaluates model performance in complex, poor-quality environments using a newly created dataset of 800+ images across 65 scene classes. Utilizes the IC3 approach to generate descriptive captions.',
    link: 'https://arxiv.org/abs/2308.02833',
  },
  {
    title: 'An Analysis of House Price Prediction Using Ensemble Learning Algorithms',
    publisher: 'Universal Wiser',
    date: 'May 29, 2023',
    description:
      'Predicts house prices by resolving data overfitting and inaccuracy issues found in previous models. Implements algorithms including XGBoost, Random Forest, SVM, and AdaBoost.',
    link: 'https://ojs.wiserpub.com/index.php/RRCS/article/view/2639',
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
    class="min-h-screen bg-black py-20 lg:py-32 border-b border-neutral-900"
  >
    <div class="max-w-[1440px] mx-auto px-6 lg:px-16 reveal-on-scroll">
      <div class="mb-20 text-center">
        <h2 class="text-amber-500 font-mono tracking-[0.4em] uppercase text-[10px] mb-4 font-bold">
          Recognition
        </h2>
        <h1 class="text-4xl md:text-7xl font-black italic uppercase tracking-tighter text-white">
          Achievements
        </h1>
        <div class="w-16 h-1 bg-amber-500 mt-6 mx-auto"></div>
      </div>

      <div class="flex flex-col lg:flex-row gap-16 lg:gap-0">
        <div class="w-full lg:w-1/2 lg:pr-12 lg:border-r lg:border-neutral-800">
          <h3
            class="text-xl font-bold mb-10 flex items-center gap-4 text-white uppercase tracking-widest"
          >
            <span class="text-amber-500 italic">01.</span> Hackathon Wins
          </h3>

          <div class="space-y-6">
            <div
              v-for="(hack, i) in hackathons"
              :key="i"
              class="bg-neutral-950/50 border border-neutral-800 p-6 rounded-xl hover:border-amber-500/40 transition-all duration-300"
            >
              <div class="flex justify-between items-start mb-4">
                <div>
                  <h4 class="text-lg font-black text-white uppercase tracking-tight">
                    {{ hack.title }}
                  </h4>
                  <p
                    class="text-amber-500 font-mono text-[10px] uppercase font-bold tracking-widest"
                  >
                    {{ hack.issuer }}
                  </p>
                </div>
                <span class="text-neutral-600 font-mono text-[10px]">{{ hack.date }}</span>
              </div>
              <p class="text-gray-400 text-xs leading-relaxed mb-4" v-html="hack.description"></p>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="tag in hack.tags"
                  :key="tag"
                  class="text-[9px] font-mono px-2 py-0.5 bg-black border border-neutral-800 rounded text-neutral-500 uppercase"
                >
                  {{ tag }}
                </span>
              </div>
            </div>
          </div>
        </div>

        <div class="w-full lg:w-1/2 lg:pl-12 flex flex-col justify-between">
          <div class="mb-16 lg:mb-0">
            <h3
              class="text-xl font-bold mb-10 flex items-center gap-4 text-white uppercase tracking-widest"
            >
              <span class="text-amber-500 italic">02.</span> Publications
            </h3>

            <div class="space-y-12">
              <div v-for="(pub, j) in publications" :key="j" class="group">
                <p class="text-[10px] font-mono text-neutral-500 mb-2 uppercase font-bold">
                  {{ pub.publisher }} | {{ pub.date }}
                </p>
                <h4
                  class="text-lg font-bold text-white group-hover:text-amber-400 transition-colors leading-snug mb-3"
                >
                  {{ pub.title }}
                </h4>
                <p class="text-xs text-gray-400 leading-relaxed mb-4">{{ pub.description }}</p>
                <a
                  :href="pub.link"
                  target="_blank"
                  class="text-amber-500 text-[10px] font-bold uppercase tracking-widest hover:text-white transition-colors flex items-center gap-2"
                >
                  View Paper <span>→</span>
                </a>
              </div>
            </div>
          </div>

          <div class="mt-16 pt-8 border-t border-neutral-900">
            <h4
              class="text-[10px] font-mono text-amber-500 uppercase tracking-[0.3em] mb-6 font-bold"
            >
              Research Focus
            </h4>
            <div class="flex flex-wrap gap-2">
              <span
                v-for="focus in focusAreas"
                :key="focus"
                class="px-3 py-1.5 bg-neutral-900 border border-neutral-800 rounded text-[10px] text-gray-400 uppercase tracking-tighter"
              >
                {{ focus }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
