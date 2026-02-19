<script setup lang="ts">
import { ref, computed } from 'vue'

const activeCategory = ref('All')
const categories = [
  'All',
  'Distributed Systems',
  'Full Stack',
  'AI & NLP',
  'Microservices',
  'Observability',
]

const projects = [
  {
    title: 'DistributedKV',
    tag: 'Distributed Systems',
    tech: ['Go', 'Raft', 'gRPC', 'Docker', 'AWS'],
    description:
      'A 5-node distributed Key-Value store implementing <strong>Raft consensus</strong> for strong consistency and 2s failover. Designed gRPC APIs with consistent hashing and optimized throughput to <strong>50K+ ops/sec</strong>.',
    visual: 'network',
  },
  {
    title: 'StreamFlow',
    tag: 'Distributed Systems',
    tech: ['Kafka', 'Flink', 'Python', 'PostgreSQL'],
    description:
      'Real-time anomaly detection platform processing <strong>50K+ events/sec</strong> with sub-second latency. Implemented Flink windowing and idempotent Python microservices for exactly-once semantics.',
    visual: 'data',
  },
  {
    title: 'LegalBill Pro',
    tag: 'Full Stack',
    tech: ['React', 'Django', 'AWS Serverless', 'PostgreSQL'],
    description:
      'Enterprise billing platform automating the payment lifecycle for <strong>12,000+ annual invoices</strong>. Architected a serverless solution using Lambda/SQS and polyglot persistence to reduce collection time from 45 to 14 days.',
    visual: 'app',
  },
  {
    title: 'Quantify',
    tag: 'AI & NLP',
    tech: ['Django', 'React', 'Transformers', 'Whisper'],
    description:
      'AI translation platform utilizing <strong>Helsinki-NLP models</strong>. Engineered a pipeline integrating <strong>Whisper (STT)</strong> and <strong>spaCy</strong> for document classification and named entity recognition.',
    visual: 'ai',
  },
  {
    title: 'CollabSpace',
    tag: 'Full Stack',
    tech: ['WebSockets', 'Redis', 'React', 'Node.js'],
    description:
      'Real-time collaboration tool for <strong>10K+ concurrent users</strong> using WebSockets and Operational Transformation (OT). Scaled Node.js via Redis Pub/Sub for sub-50ms latency.',
    visual: 'code',
  },
  {
    title: 'ShopFlow',
    tag: 'Microservices',
    tech: ['Node.js', 'K8s', 'RabbitMQ', 'PostgreSQL'],
    description:
      'E-commerce platform with 8 microservices and <strong>Saga pattern</strong> for distributed transactions. Processed 50K+ monthly transactions with Stripe integration and 99.95% uptime on Kubernetes.',
    visual: 'network',
  },
  {
    title: 'OpsDash',
    tag: 'Observability',
    tech: ['FastAPI', 'Prometheus', 'Grafana', 'React'],
    description:
      'Observability platform aggregating <strong>5M+ daily metrics</strong> from 100+ exporters. Built with FastAPI and TimescaleDB for sub-second metric querying and anomaly detection.',
    visual: 'data',
  },
]

const filteredProjects = computed(() => {
  if (activeCategory.value === 'All') return projects
  return projects.filter((p) => p.tag === activeCategory.value)
})

const setCategory = (category: string) => {
  activeCategory.value = category
}
</script>

<template>
  <section
    id="projects"
    class="min-h-screen bg-black border-b border-neutral-900 overflow-hidden py-20"
  >
    <div class="max-w-[1440px] px-6 lg:px-16 mx-auto w-full reveal-on-scroll">
      <div class="mb-16 text-center">
        <h2 class="text-xs uppercase tracking-[0.6em] text-amber-500 mb-4 font-bold">Portfolio</h2>
        <h1 class="text-4xl md:text-7xl font-black tracking-tighter italic text-white">
          FEATURED PROJECTS
        </h1>
        <div class="w-20 h-1 bg-amber-400 mx-auto mt-6 rounded-full"></div>
      </div>

      <!-- Filter Tabs -->
      <div class="flex flex-wrap justify-center gap-4 mb-16">
        <button
          v-for="category in categories"
          :key="category"
          @click="setCategory(category)"
          class="px-6 py-2 rounded-full text-xs font-mono uppercase tracking-widest border transition-all duration-300"
          :class="
            activeCategory === category
              ? 'border-amber-500 bg-amber-500/10 text-amber-500 shadow-[0_0_15px_rgba(251,191,36,0.3)]'
              : 'border-neutral-800 text-neutral-500 hover:border-neutral-600 hover:text-neutral-300'
          "
        >
          {{ category }}
        </button>
      </div>

      <!-- Projects Grid -->
      <TransitionGroup
        name="project-grid"
        tag="div"
        class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8"
      >
        <div
          v-for="project in filteredProjects"
          :key="project.title"
          class="group relative bg-neutral-900/40 border border-neutral-800 rounded-2xl overflow-hidden hover:border-amber-500/50 transition-all duration-500 flex flex-col h-full"
        >
          <!-- Visual Header -->
          <div
            class="bg-black/50 h-48 border-b border-neutral-800 flex items-center justify-center p-6 relative overflow-hidden group-hover:bg-amber-500/5 transition-colors duration-500"
          >
            <!-- Visualizations based on type -->
            <div
              v-if="project.visual === 'network'"
              class="relative w-full h-full flex items-center justify-center scale-75"
            >
              <div
                class="absolute inset-0 border border-amber-500/20 rounded-full animate-[spin_10s_linear_infinite]"
              ></div>
              <div
                class="absolute inset-4 border border-amber-500/10 rounded-full animate-[spin_15s_linear_infinite_reverse]"
              ></div>
              <div
                class="w-16 h-16 bg-amber-500/10 rounded-full flex items-center justify-center backdrop-blur-sm border border-amber-500/40"
              >
                <span class="text-[8px] font-mono text-amber-500">NET</span>
              </div>
            </div>

            <div
              v-else-if="project.visual === 'data'"
              class="w-full max-w-[200px] h-24 flex items-center justify-center gap-1"
            >
              <div class="w-1/5 bg-amber-500/20 h-1/4 animate-pulse rounded-t"></div>
              <div class="w-1/5 bg-amber-500/40 h-1/2 animate-pulse delay-75 rounded-t"></div>
              <div class="w-1/5 bg-amber-500/60 h-3/4 animate-pulse delay-150 rounded-t"></div>
              <div class="w-1/5 bg-amber-500/30 h-1/3 animate-pulse delay-100 rounded-t"></div>
              <div class="w-1/5 bg-amber-500/80 h-full animate-pulse delay-200 rounded-t"></div>
            </div>

            <div
              v-else-if="project.visual === 'ai'"
              class="relative w-32 h-32 flex items-center justify-center"
            >
              <div
                class="absolute inset-0 rounded-full border border-amber-500/10 animate-ping"
              ></div>
              <div
                class="w-16 h-16 rounded-full border border-amber-500/30 flex items-center justify-center"
              >
                <span class="text-[8px] font-mono text-amber-500">AI</span>
              </div>
            </div>

            <div
              v-else-if="project.visual === 'code'"
              class="w-full max-w-[200px] bg-black border border-neutral-800 rounded p-3 font-mono text-[8px] text-gray-500 opacity-80 group-hover:opacity-100 transition-opacity"
            >
              <p>
                <span class="text-amber-500">func</span> <span class="text-blue-400">main</span>() {
              </p>
              <p class="pl-2">go <span class="text-purple-400">process()</span></p>
              <p>}</p>
            </div>

            <div
              v-else
              class="text-amber-500 font-mono text-xs uppercase tracking-widest border border-amber-500/30 px-3 py-1 rounded"
            >
              {{ project.tag }}
            </div>

            <!-- Hover Overlay -->
            <div
              class="absolute inset-6 bg-amber-500/10 blur-2xl opacity-0 group-hover:opacity-100 transition-opacity duration-500"
            ></div>
          </div>

          <!-- Content Body -->
          <div class="p-6 flex flex-col flex-grow">
            <div class="flex justify-between items-start mb-4">
              <span
                class="px-2 py-0.5 bg-neutral-800 text-amber-500 text-[9px] font-bold rounded tracking-widest uppercase border border-neutral-700"
              >
                {{ project.tag }}
              </span>
            </div>

            <h3
              class="text-2xl font-bold text-white mb-3 group-hover:text-amber-400 transition-colors"
            >
              {{ project.title }}
            </h3>

            <p
              class="text-sm text-gray-400 leading-relaxed font-light mb-6 flex-grow"
              v-html="project.description"
            ></p>

            <!-- Tech Stack -->
            <div class="flex flex-wrap gap-2 mt-auto pt-4 border-t border-neutral-800/50">
              <span
                v-for="(tech, tIndex) in project.tech"
                :key="tIndex"
                class="text-[10px] font-mono text-neutral-500"
              >
                #{{ tech }}
              </span>
            </div>
          </div>
        </div>
      </TransitionGroup>
    </div>
  </section>
</template>

<style scoped>
/* Project Grid Transitions */
.project-grid-move,
.project-grid-enter-active,
.project-grid-leave-active {
  transition: all 0.5s cubic-bezier(0.55, 0, 0.1, 1);
}

.project-grid-enter-from,
.project-grid-leave-to {
  opacity: 0;
  transform: scale(0.9);
}

.project-grid-leave-active {
  position: absolute;
  width: 100%; /* Ensure it doesn't collapse */
  z-index: 0;
}
</style>
