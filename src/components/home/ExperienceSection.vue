<script setup lang="ts">
import { ref, onMounted } from 'vue'

const workHistory = [
  {
    company: 'Scholarship Auditions',
    role: 'Software Engineer',
    location: 'Nashville, TN',
    period: 'Oct 2024 – Present',
    bullets: [
      'Architected a microservices migration from Webflow to <strong>Django/Angular with SSR</strong>, achieving a <strong>200% SEO visibility boost</strong> and reducing load times by 65%.',
      'Engineered an elastic, cost-optimized <strong>AWS ECS Fargate</strong> architecture with Redis to handle <strong>100K+ daily requests</strong> with 99.9% uptime.',
      'Built a full observability stack using <strong>Prometheus, Grafana, and CloudWatch</strong>, reducing Mean Time to Detection (MTTD) from 45 mins to <5 mins.',
      'Designed a <strong>serverless onboarding pipeline</strong> (Lambda, S3, SQS) for 40,000+ records with idempotent operations and DLQs.',
      'Implemented distributed <strong>Celery task systems</strong> reducing queue latency by 40%. Established CI/CD via GitHub Actions reducing deploy time by 85%.',
    ],
  },
  {
    company: 'Scholarship Auditions',
    role: 'Software Engineer Intern',
    location: 'Nashville, TN',
    period: 'Aug 2024 – Oct 2024',
    bullets: [
      'Designed scalable <strong>RESTful APIs</strong> using DRF and S3/CloudFront, supporting 16,000+ active users.',
      'Applied <strong>TDD with pytest</strong> to achieve 85%+ code coverage and contributed to Agile sprints via JIRA.',
    ],
  },
  {
    company: 'Avairsense',
    role: 'Backend Engineer Intern',
    location: 'Bangalore, India',
    period: 'Nov 2021 – Feb 2022',
    bullets: [
      'Engineered high-throughput <strong>CV pipeline (Python, YOLOv5)</strong> processing 50+ concurrent video streams with sub-200ms latency.',
      'Built <strong>FastAPI endpoints</strong> with MongoDB (TTL/Geospatial) for real-time detection metadata ingestion.',
      'Reduced cloud compute costs by <strong>25%</strong> through batch processing profiling and dynamic resource allocation.',
    ],
  },
]

const workExpanded = ref<Record<number, boolean>>({})

const toggleWork = (index: number) => {
  workExpanded.value[index] = !workExpanded.value[index]
}

onMounted(() => {
  // Let them start closed for clean reveal, or open first one
  setTimeout(() => {
    workExpanded.value[0] = true
  }, 500)
})
</script>

<template>
  <section
    id="experience"
    class="min-h-screen bg-neutral-950 py-32 border-y border-neutral-900 overflow-hidden"
  >
    <div class="max-w-7xl mx-auto px-6 lg:px-24 w-full">
      <div class="flex flex-col lg:flex-row gap-16 lg:gap-24">
        <!-- Left: Title (Sticky) -->
        <div class="lg:w-1/3">
          <div class="sticky top-32">
            <h2
              class="text-amber-500 font-mono tracking-[0.4em] uppercase text-[10px] mb-4 font-bold"
            >
              Career Path
            </h2>
            <h1
              class="text-4xl md:text-6xl font-black italic uppercase tracking-tighter text-white mb-8"
            >
              Work<br /><span class="text-neutral-700">History</span>
            </h1>
            <div class="w-16 h-1 bg-amber-500 rounded-full mb-8"></div>
            <p class="text-gray-400 text-sm leading-relaxed">
              Solving complex problems across distributed systems, cloud infrastructure, and backend
              engineering.
            </p>
          </div>
        </div>

        <!-- Right: Timeline & Cards -->
        <div class="lg:w-2/3 relative">
          <!-- Vertical Line -->
          <div class="absolute left-[19px] top-4 bottom-0 w-[2px] bg-neutral-800"></div>

          <div class="flex flex-col gap-12">
            <div v-for="(job, index) in workHistory" :key="index" class="relative pl-12 group">
              <!-- Timeline Dot -->
              <div
                class="absolute left-0 top-6 w-10 h-10 -ml-[0.5px] z-10 flex items-center justify-center transition-all duration-300"
                :class="workExpanded[index] ? 'scale-110' : 'scale-100 group-hover:scale-110'"
              >
                <div
                  class="w-3 h-3 rounded-full bg-black border-2 transition-colors duration-300"
                  :class="
                    workExpanded[index]
                      ? 'border-amber-500 bg-amber-500'
                      : 'border-neutral-600 group-hover:border-amber-500/50'
                  "
                ></div>
              </div>

              <!-- Card -->
              <div
                @click="toggleWork(index)"
                class="bg-neutral-900/30 border border-neutral-800 rounded-2xl overflow-hidden hover:border-amber-500/30 transition-all duration-300 cursor-pointer"
                :class="
                  workExpanded[index]
                    ? 'bg-neutral-900/50 border-amber-500/30 shadow-[0_0_30px_rgba(0,0,0,0.3)]'
                    : ''
                "
              >
                <!-- Header -->
                <div
                  class="p-6 md:p-8 flex flex-col md:flex-row md:items-center justify-between gap-4"
                >
                  <div>
                    <h3
                      class="text-xl font-bold text-white mb-1 transition-colors"
                      :class="workExpanded[index] ? 'text-amber-400' : ''"
                    >
                      {{ job.role }}
                    </h3>
                    <p class="text-sm font-mono text-neutral-400 uppercase tracking-wider">
                      {{ job.company }}
                    </p>
                  </div>
                  <div
                    class="text-xs font-mono text-neutral-500 bg-black/30 px-3 py-1.5 rounded border border-neutral-800 whitespace-nowrap self-start md:self-auto"
                  >
                    {{ job.period }}
                  </div>
                </div>

                <!-- Collapsible Body -->
                <div
                  class="grid transition-[grid-template-rows] duration-500 ease-in-out"
                  :class="workExpanded[index] ? 'grid-rows-[1fr]' : 'grid-rows-[0fr]'"
                >
                  <div class="overflow-hidden">
                    <div class="px-6 md:px-8 pb-8 pt-0 border-t border-neutral-800/50 mt-2">
                      <h4
                        class="text-[10px] font-mono text-amber-500/70 uppercase tracking-widest mb-4 mt-6"
                      >
                        Key Responsibilities
                      </h4>
                      <ul class="space-y-3">
                        <li
                          v-for="(bullet, bIndex) in job.bullets"
                          :key="bIndex"
                          class="flex gap-3 text-sm text-gray-300 leading-relaxed group/item"
                        >
                          <span
                            class="text-amber-500/50 mt-1.5 text-[10px] group-hover/item:text-amber-500 transition-colors"
                            >▹</span
                          >
                          <span v-html="bullet"></span>
                        </li>
                      </ul>
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
