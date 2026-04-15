<script setup lang="ts">
import { ref, onMounted } from 'vue'

const workHistory = [
  {
    company: 'Scholarship Auditions',
    role: 'Software Engineer – Full Stack & ML Systems',
    location: 'Nashville, TN',
    period: 'Jan 2025 – Present',
    bullets: [
      'Migrated legacy Webflow + Angular to <strong>Django & Angular on AWS</strong> via zero-downtime rollout, eliminating $2.5K/mo vendor costs and <strong>cutting page load 4.2s → 1.5s</strong>.',
      'Improved user acquisition & engagement by optimizing rendering flows and SSR pages, driving <strong>3x organic search growth</strong> in 3 months.',
      'Scaled platform to <strong>100K+ daily users</strong> at 99.9% uptime using ECS Fargate and Redis caching; reduced annual cloud spend <strong>35% (~$18K)</strong>.',
      'Designed fault-tolerant async ingestion (S3, SQS, Lambda, SES) for <strong>60K+ records</strong>, eliminating peak-time database contention.',
      'Built operational dashboards with <strong>Prometheus + Grafana</strong>, reducing incident detection time from 45 min to 5 min.',
    ],
  },
  {
    company: 'Scholarship Auditions',
    role: 'Software Engineer Intern',
    location: 'Nashville, TN',
    period: 'Aug 2024 – Dec 2024',
    bullets: [
      'Accelerated product velocity by shipping end-to-end <strong>Angular & Django workflows</strong> to support rapid onboarding for 16K+ users.',
      'Stabilized performance during traffic bursts by resolving N+1 bottlenecks via <strong>select_related</strong>, slashing API latency 40%.',
    ],
  },
  {
    company: 'Law Office of Jenny Cochrane',
    role: 'Software Engineer (Contract)',
    location: 'Kirkland, WA',
    period: 'Jan 2024 – Jun 2024',
    bullets: [
      'Shipped LegalBill Pro on <strong>React + AWS Serverless</strong>, automating 12K+ annual invoices and cutting collection time 45 → 14 days (69% faster).',
      'Built an <strong>AES-256 encrypted document vault</strong> with full audit trail and automated payment reconciliation via Stripe and CloudWatch.',
      'Designed polyglot persistence: <strong>DynamoDB</strong> for billing event logs and <strong>PostgreSQL</strong> for ACID-compliant records.',
    ],
  },
  {
    company: 'Avairsense (YC W22)',
    role: 'Software Engineer',
    location: 'Bangalore, India',
    period: 'Jul 2021 – Jul 2023',
    bullets: [
      'Built a real-time computer vision platform using <strong>YOLOv5 + ByteTrack</strong> across 80+ concurrent CCTV feeds on a GPU cluster, maintaining sub-150ms production inference latency.',
      'Engineered <strong>AWS IoT Core + SQS pipelines</strong> with retry and failover, guaranteeing zero event loss across 300+ edge devices.',
      'Automated OTA deployment via <strong>Kubernetes, ONNX Runtime, and GitHub Actions</strong>, cutting multi-day rollouts to 2 hours.',
      'Raised anomaly detection accuracy 18% by building ML infrastructure: annotation pipelines and eval harnesses.',
    ],
  },
  {
    company: 'Avairsense (YC W22)',
    role: 'Software Engineer Intern',
    location: 'Bangalore, India',
    period: 'Mar 2021 – Jun 2021',
    bullets: [
      'Ramped into pre-launch codebase in 6 weeks; shipped <strong>YOLOv5 GPU inference</strong> for 50+ streams at sub-200ms latency.',
      'Built <strong>FastAPI services</strong> with MongoDB geospatial indexing and TTL collections, cutting spatial query latency 60%.',
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
    class="min-h-screen bg-black border-t border-neutral-900 py-32 relative overflow-hidden flex items-center justify-center text-center"
  >
    <!-- Background Elements (Matching Education/Hero) -->
    <div class="absolute inset-0 z-0">
      <div
        class="absolute inset-0 bg-[linear-gradient(to_right,#80808012_1px,transparent_1px),linear-gradient(to_bottom,#80808012_1px,transparent_1px)] bg-[size:40px_40px]"
      ></div>
      <!-- Subtle glow in center -->
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
          Career Path
        </h2>
        <h1
          class="text-5xl lg:text-7xl xl:text-8xl font-black italic uppercase tracking-tighter text-white leading-none"
        >
          Work<span class="text-neutral-700">History</span>
        </h1>
        <div class="w-20 lg:w-32 h-1 bg-amber-500 rounded-full mt-8"></div>
        <p class="text-gray-400 text-lg lg:text-xl leading-relaxed font-light max-w-2xl mt-8">
          Solving complex problems across distributed systems, cloud infrastructure, and backend
          engineering.
        </p>
      </div>

      <!-- Experience Cards Stack (Accordion) -->
      <div class="w-full max-w-4xl flex flex-col gap-6 lg:gap-8">
        <div
          v-for="(job, index) in workHistory"
          :key="index"
          class="group relative w-full text-left"
        >
          <div
            @click="toggleWork(index)"
            class="relative bg-neutral-950/40 border rounded-3xl overflow-hidden transition-all duration-500 cursor-pointer flex flex-col shadow-[0_0_50px_rgba(0,0,0,0.5)]"
            :class="
              workExpanded[index]
                ? 'border-amber-500/50 bg-neutral-900/60 shadow-[0_0_40px_rgba(251,191,36,0.15)] scale-[1.01]'
                : 'border-neutral-800 hover:border-amber-500/30 hover:bg-neutral-900/40'
            "
          >
            <!-- Header (Always Visible) -->
            <div
              class="p-8 lg:p-10 flex flex-col md:flex-row md:items-center justify-between gap-6 relative z-10"
            >
              <div class="flex flex-col gap-2">
                <h3
                  class="text-2xl lg:text-3xl font-bold tracking-tight transition-colors duration-300"
                  :class="
                    workExpanded[index] ? 'text-amber-400' : 'text-white group-hover:text-amber-100'
                  "
                >
                  {{ job.role }}
                </h3>
                <p
                  class="text-[11px] lg:text-xs font-mono text-neutral-400 uppercase tracking-[0.2em] italic"
                >
                  {{ job.company }} <span class="pl-2 pr-2 text-neutral-600">|</span>
                  {{ job.location }}
                </p>
              </div>

              <div class="flex items-center gap-4 self-start md:self-auto">
                <div
                  class="text-[10px] font-mono text-neutral-500 bg-neutral-900/80 px-4 py-2 rounded-full border border-neutral-800 whitespace-nowrap uppercase tracking-wider"
                >
                  {{ job.period }}
                </div>
                <!-- Expansion Chevron -->
                <div
                  class="w-8 h-8 rounded-full border flex items-center justify-center transition-all duration-300"
                  :class="
                    workExpanded[index]
                      ? 'border-amber-500/50 text-amber-500 bg-amber-500/10 rotate-180'
                      : 'border-neutral-700 text-neutral-500 group-hover:border-amber-500/30 group-hover:text-amber-500'
                  "
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-4 w-4"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M19 9l-7 7-7-7"
                    />
                  </svg>
                </div>
              </div>
            </div>

            <!-- Collapsible Body -->
            <div
              class="grid transition-[grid-template-rows] duration-500 ease-in-out relative z-10"
              :class="workExpanded[index] ? 'grid-rows-[1fr]' : 'grid-rows-[0fr]'"
            >
              <div class="overflow-hidden">
                <div
                  class="px-8 lg:px-10 pb-10 pt-2 opacity-0 transition-opacity duration-700 delay-100"
                  :class="workExpanded[index] ? 'opacity-100' : 'opacity-0'"
                >
                  <div
                    class="w-full h-px bg-gradient-to-r from-neutral-800/20 via-neutral-700 to-neutral-800/20 mb-8"
                  ></div>

                  <h4
                    class="text-[10px] font-mono text-amber-500/70 uppercase tracking-[0.3em] mb-6 font-bold flex items-center gap-3"
                  >
                    Key Responsibilities
                  </h4>

                  <ul class="space-y-4">
                    <li
                      v-for="(bullet, bIndex) in job.bullets"
                      :key="bIndex"
                      class="flex gap-4 text-sm lg:text-base text-gray-300 xl:text-gray-400 leading-relaxed group/item items-start"
                    >
                      <span
                        class="text-amber-500/40 mt-1 text-xs group-hover/item:text-amber-500 transition-colors"
                        >▹</span
                      >
                      <span class="flex-1" v-html="bullet"></span>
                      <!-- Safe html rendering based on original setup -->
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
