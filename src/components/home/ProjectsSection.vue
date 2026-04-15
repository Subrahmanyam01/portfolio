<script setup lang="ts">
import { ref, computed } from 'vue'

const activeCategory = ref('All')
const hoveredProject = ref<string | null>(null)

const categories = [
  'All',
  'Distributed Systems',
  'Full Stack',
  'AI & NLP',
  'Microservices',
  'Observability',
]

interface Project {
  title: string
  tag: string
  tech: string[]
  description: string
  metrics: { label: string; value: string }[]
  visual: string
  featured?: boolean
  github?: string
  live?: string
  accentColor: string
}

const projects: Project[] = [
  {
    title: 'DistributedKV',
    tag: 'Distributed Systems',
    tech: ['Go', 'Raft', 'gRPC', 'Docker', 'AWS'],
    description:
      'A 5-node distributed Key-Value store implementing <strong>Raft consensus</strong> for strong consistency and 2s failover. Designed gRPC APIs with consistent hashing and optimized throughput.',
    metrics: [
      { label: 'Throughput', value: '50K+ ops/s' },
      { label: 'Failover', value: '< 2s' },
      { label: 'Nodes', value: '5-node' },
    ],
    visual: 'network',
    featured: true,
    github: '#',
    accentColor: '#fbbf24',
  },
  {
    title: 'InsightEngine',
    tag: 'AI & NLP',
    tech: ['Angular', 'FastAPI', 'Pinecone', 'LangChain', 'AWS'],
    description:
      'Information retrieval system with <strong>hybrid search</strong> (Keyword + Vector) over 50K+ documents. Integrated re-ranking pipelines achieving sub-500ms p99 latency.',
    metrics: [
      { label: 'Recall ↑', value: '25%' },
      { label: 'p99 Latency', value: '420ms' },
      { label: 'Docs', value: '50K+' },
    ],
    visual: 'ai',
    github: '#',
    accentColor: '#fbbf24',
  },
  {
    title: 'Quantify',
    tag: 'AI & NLP',
    tech: ['Django', 'React', 'Redis', 'Whisper', 'HuggingFace'],
    description:
      'AI translation & transcription platform. Built a pipeline with <strong>Whisper (STT)</strong> and Helsinki-NLP models. Model quantization reduced GPU memory usage by 30%.',
    metrics: [
      { label: 'Memory ↓', value: '30%' },
      { label: 'Latency', value: '800ms' },
      { label: 'Langs', value: '200+' },
    ],
    visual: 'data',
    github: '#',
    accentColor: '#f59e0b',
  },
  {
    title: 'LegalBill Pro',
    tag: 'Full Stack',
    tech: ['React', 'Django', 'AWS Serverless', 'PostgreSQL'],
    description:
      'Enterprise billing platform automating 12K+ annual invoices. Features an <strong>AES-256 encrypted vault</strong> and automated reconciliation via Stripe.',
    metrics: [
      { label: 'Collection ↓', value: '69%' },
      { label: 'Time', value: '45d → 14d' },
    ],
    visual: 'app',
    github: '#',
    accentColor: '#d97706',
  },
  {
    title: 'CollabSpace',
    tag: 'Full Stack',
    tech: ['WebSockets', 'Redis', 'React', 'Node.js'],
    description:
      'Real-time collaboration tool for <strong>10K+ concurrent users</strong> using WebSockets and Operational Transformation (OT). Scaled Node.js via Redis Pub/Sub for sub-50ms latency.',
    metrics: [
      { label: 'Concurrent', value: '10K+' },
      { label: 'Latency', value: '< 50ms' },
    ],
    visual: 'code',
    github: '#',
    accentColor: '#fbbf24',
  },
  {
    title: 'ShopFlow',
    tag: 'Microservices',
    tech: ['Node.js', 'K8s', 'RabbitMQ', 'PostgreSQL'],
    description:
      'E-commerce platform with 8 microservices and <strong>Saga pattern</strong> for distributed transactions. Processed 50K+ monthly transactions with Stripe integration.',
    metrics: [
      { label: 'Uptime', value: '99.95%' },
      { label: 'Tx/month', value: '50K+' },
    ],
    visual: 'network',
    github: '#',
    accentColor: '#f59e0b',
  },
]

const featuredProject = computed(() => projects.find((p) => p.featured))
const regularProjects = computed(() => projects.filter((p) => !p.featured))

const filteredProjects = computed(() => {
  if (activeCategory.value === 'All') return regularProjects.value
  return regularProjects.value.filter((p) => p.tag === activeCategory.value)
})

const setCategory = (category: string) => {
  activeCategory.value = category
}

const techColorMap: Record<string, string> = {
  Go: 'text-cyan-400 border-cyan-400/30 bg-cyan-400/5',
  Raft: 'text-purple-400 border-purple-400/30 bg-purple-400/5',
  gRPC: 'text-blue-400 border-blue-400/30 bg-blue-400/5',
  Docker: 'text-sky-400 border-sky-400/30 bg-sky-400/5',
  AWS: 'text-orange-400 border-orange-400/30 bg-orange-400/5',
  Kafka: 'text-red-400 border-red-400/30 bg-red-400/5',
  Flink: 'text-pink-400 border-pink-400/30 bg-pink-400/5',
  Python: 'text-yellow-400 border-yellow-400/30 bg-yellow-400/5',
  PostgreSQL: 'text-indigo-400 border-indigo-400/30 bg-indigo-400/5',
  React: 'text-cyan-300 border-cyan-300/30 bg-cyan-300/5',
  Django: 'text-green-400 border-green-400/30 bg-green-400/5',
  Transformers: 'text-violet-400 border-violet-400/30 bg-violet-400/5',
  Whisper: 'text-rose-400 border-rose-400/30 bg-rose-400/5',
  spaCy: 'text-lime-400 border-lime-400/30 bg-lime-400/5',
  WebSockets: 'text-emerald-400 border-emerald-400/30 bg-emerald-400/5',
  Redis: 'text-red-300 border-red-300/30 bg-red-300/5',
  'Node.js': 'text-green-300 border-green-300/30 bg-green-300/5',
  K8s: 'text-blue-500 border-blue-500/30 bg-blue-500/5',
  RabbitMQ: 'text-orange-300 border-orange-300/30 bg-orange-300/5',
  FastAPI: 'text-teal-400 border-teal-400/30 bg-teal-400/5',
  Prometheus: 'text-orange-500 border-orange-500/30 bg-orange-500/5',
  Grafana: 'text-amber-300 border-amber-300/30 bg-amber-300/5',
  TimescaleDB: 'text-blue-300 border-blue-300/30 bg-blue-300/5',
  Redux: 'text-purple-500 border-purple-500/30 bg-purple-500/5',
  'AWS Serverless': 'text-orange-400 border-orange-400/30 bg-orange-400/5',
}

const getTechColor = (tech: string) =>
  techColorMap[tech] || 'text-neutral-400 border-neutral-600/30 bg-neutral-600/5'
</script>

<template>
  <section
    id="projects"
    class="min-h-screen bg-black border-b border-neutral-900 overflow-hidden py-24 lg:py-32 relative"
  >
    <!-- Background grid -->
    <div class="absolute inset-0 z-0 pointer-events-none">
      <div
        class="absolute inset-0 bg-[linear-gradient(to_right,#80808008_1px,transparent_1px),linear-gradient(to_bottom,#80808008_1px,transparent_1px)] bg-[size:40px_40px]"
      ></div>
      <div
        class="absolute top-1/3 left-1/2 -translate-x-1/2 w-[80vw] h-[40vw] bg-amber-500/3 rounded-full blur-[150px]"
      ></div>
    </div>

    <div class="max-w-[1440px] px-6 lg:px-16 mx-auto w-full relative z-10 reveal-on-scroll">
      <!-- Section Header -->
      <div class="mb-16 lg:mb-20">
        <h2 class="text-xs uppercase tracking-[0.6em] text-amber-500 mb-4 font-bold font-mono">
          Portfolio
        </h2>
        <div class="flex flex-col lg:flex-row lg:items-end lg:justify-between gap-6">
          <h1
            class="text-5xl md:text-7xl xl:text-8xl font-black tracking-tighter italic text-white leading-none"
          >
            FEATURED <br /><span class="text-neutral-700">PROJECTS</span>
          </h1>
          <p
            class="text-gray-400 text-base lg:text-lg leading-relaxed font-light max-w-md lg:text-right"
          >
            A curated collection of systems I've designed and shipped — spanning distributed
            infrastructure, AI pipelines, and real-time platforms.
          </p>
        </div>
        <div class="w-24 h-0.5 bg-gradient-to-r from-amber-500 to-transparent mt-10"></div>
      </div>

      <!-- FEATURED PROJECT (Hero Card) -->
      <div
        v-if="featuredProject"
        class="group relative mb-16 rounded-3xl overflow-hidden border border-neutral-800 bg-neutral-950/60 hover:border-amber-500/40 transition-all duration-700 hover:shadow-[0_0_80px_rgba(251,191,36,0.08)]"
        @mouseenter="hoveredProject = featuredProject!.title"
        @mouseleave="hoveredProject = null"
      >
        <!-- Ambient glow on hover -->
        <div
          class="absolute inset-0 bg-gradient-to-br from-amber-500/5 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-700 pointer-events-none"
        ></div>

        <div class="grid grid-cols-1 lg:grid-cols-5 min-h-[360px]">
          <!-- Visual Panel -->
          <div
            class="lg:col-span-2 relative bg-black/60 flex items-center justify-center p-12 border-b lg:border-b-0 lg:border-r border-neutral-800/60 overflow-hidden min-h-[240px]"
          >
            <!-- Network Visualization -->
            <div class="relative w-full h-full flex items-center justify-center">
              <!-- Outer rings -->
              <div
                class="absolute w-56 h-56 border border-amber-500/10 rounded-full animate-spin-ultra-slow"
              ></div>
              <div
                class="absolute w-40 h-40 border border-amber-500/15 rounded-full animate-spin-ultra-slow-reverse"
              ></div>
              <div
                class="absolute w-24 h-24 border border-amber-500/25 rounded-full animate-pulse-slow"
              ></div>

              <!-- Center hub -->
              <div
                class="relative w-16 h-16 bg-amber-500/10 border border-amber-500/50 rounded-full flex items-center justify-center backdrop-blur-sm shadow-[0_0_30px_rgba(251,191,36,0.2)] group-hover:shadow-[0_0_50px_rgba(251,191,36,0.3)] transition-shadow duration-700"
              >
                <span class="text-[9px] font-mono text-amber-500 font-bold tracking-widest"
                  >KV</span
                >
              </div>

              <!-- Orbiting nodes -->
              <div class="node-orbit absolute" style="--orbit-d: 90px; --orbit-delay: 0s">
                <div
                  class="w-3 h-3 bg-amber-500/30 border border-amber-500/60 rounded-full shadow-[0_0_8px_rgba(251,191,36,0.4)]"
                ></div>
              </div>
              <div class="node-orbit absolute" style="--orbit-d: 90px; --orbit-delay: -3.3s">
                <div class="w-2 h-2 bg-amber-500/20 border border-amber-500/40 rounded-full"></div>
              </div>
              <div class="node-orbit absolute" style="--orbit-d: 90px; --orbit-delay: -6.6s">
                <div
                  class="w-2.5 h-2.5 bg-amber-500/25 border border-amber-500/50 rounded-full"
                ></div>
              </div>

              <!-- Data packets / lines -->
              <svg
                class="absolute inset-0 w-full h-full pointer-events-none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <line
                  x1="50%"
                  y1="50%"
                  x2="20%"
                  y2="20%"
                  stroke="#fbbf24"
                  stroke-width="0.5"
                  stroke-dasharray="3 8"
                  opacity="0.2"
                />
                <line
                  x1="50%"
                  y1="50%"
                  x2="80%"
                  y2="25%"
                  stroke="#fbbf24"
                  stroke-width="0.5"
                  stroke-dasharray="3 8"
                  opacity="0.2"
                />
                <line
                  x1="50%"
                  y1="50%"
                  x2="80%"
                  y2="75%"
                  stroke="#fbbf24"
                  stroke-width="0.5"
                  stroke-dasharray="3 8"
                  opacity="0.2"
                />
                <line
                  x1="50%"
                  y1="50%"
                  x2="20%"
                  y2="75%"
                  stroke="#fbbf24"
                  stroke-width="0.5"
                  stroke-dasharray="3 8"
                  opacity="0.2"
                />
                <line
                  x1="50%"
                  y1="50%"
                  x2="50%"
                  y2="10%"
                  stroke="#fbbf24"
                  stroke-width="0.5"
                  stroke-dasharray="3 8"
                  opacity="0.2"
                />
              </svg>

              <!-- FEATURED badge -->
              <div
                class="absolute top-4 left-4 px-3 py-1 bg-amber-500/10 border border-amber-500/30 rounded-full"
              >
                <span
                  class="text-[9px] font-mono font-bold text-amber-500 tracking-[0.3em] uppercase"
                  >★ Featured</span
                >
              </div>
            </div>
          </div>

          <!-- Content Panel -->
          <div class="lg:col-span-3 p-8 lg:p-12 flex flex-col justify-between">
            <div>
              <!-- Tag + Title -->
              <div class="flex items-center gap-3 mb-5">
                <span
                  class="text-[9px] font-mono font-bold text-amber-500/70 uppercase tracking-[0.3em] px-3 py-1 border border-amber-500/20 rounded-full bg-amber-500/5"
                >
                  {{ featuredProject.tag }}
                </span>
              </div>

              <h3
                class="text-4xl lg:text-5xl font-black italic tracking-tighter text-white mb-4 group-hover:text-amber-300 transition-colors duration-500"
              >
                {{ featuredProject.title }}
              </h3>

              <p
                class="text-gray-400 text-base leading-relaxed font-light mb-8 max-w-lg"
                v-html="featuredProject.description"
              ></p>

              <!-- Metrics row -->
              <div class="grid grid-cols-3 gap-4 mb-8">
                <div
                  v-for="metric in featuredProject.metrics"
                  :key="metric.label"
                  class="bg-neutral-900/60 border border-neutral-800 rounded-xl p-4 text-center group-hover:border-amber-500/20 transition-colors duration-500"
                >
                  <p class="text-xl font-black text-amber-400 mb-1">{{ metric.value }}</p>
                  <p class="text-[9px] font-mono text-neutral-500 uppercase tracking-widest">
                    {{ metric.label }}
                  </p>
                </div>
              </div>
            </div>

            <div
              class="flex flex-col sm:flex-row sm:items-center justify-between gap-6 pt-6 border-t border-neutral-800/50"
            >
              <!-- Tech Stack -->
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="tech in featuredProject.tech"
                  :key="tech"
                  class="text-[10px] font-mono px-2.5 py-1 border rounded-full transition-all duration-300"
                  :class="getTechColor(tech)"
                >
                  {{ tech }}
                </span>
              </div>

              <!-- CTA Buttons -->
              <div class="flex gap-3 shrink-0">
                <a
                  v-if="featuredProject.github"
                  :href="featuredProject.github"
                  class="flex items-center gap-2 px-5 py-2.5 bg-amber-500 text-black text-xs font-black uppercase tracking-widest rounded-xl hover:bg-amber-400 transition-colors duration-300 group/btn"
                >
                  <svg class="w-3.5 h-3.5" fill="currentColor" viewBox="0 0 24 24">
                    <path
                      d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"
                    />
                  </svg>
                  GitHub
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Category Filter -->
      <div class="flex flex-wrap gap-2 mb-12">
        <button
          v-for="category in categories"
          :key="category"
          @click="setCategory(category)"
          class="px-5 py-2 rounded-full text-[10px] font-mono uppercase tracking-[0.2em] border transition-all duration-300"
          :class="
            activeCategory === category
              ? 'border-amber-500 bg-amber-500/10 text-amber-500 shadow-[0_0_20px_rgba(251,191,36,0.2)]'
              : 'border-neutral-800 text-neutral-500 hover:border-neutral-700 hover:text-neutral-300'
          "
        >
          {{ category }}
        </button>
      </div>

      <!-- Projects Bento Grid -->
      <TransitionGroup
        name="project-grid"
        tag="div"
        class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-5"
      >
        <div
          v-for="project in filteredProjects"
          :key="project.title"
          class="group relative bg-neutral-950/60 border border-neutral-800 rounded-2xl overflow-hidden hover:border-amber-500/40 transition-all duration-500 flex flex-col hover:shadow-[0_0_40px_rgba(251,191,36,0.06)] cursor-default"
          @mouseenter="hoveredProject = project.title"
          @mouseleave="hoveredProject = null"
        >
          <!-- Visual Header -->
          <div
            class="h-40 border-b border-neutral-800/60 flex items-center justify-center p-6 relative overflow-hidden bg-black/40 group-hover:bg-amber-500/3 transition-colors duration-500"
          >
            <!-- network visual -->
            <div
              v-if="project.visual === 'network'"
              class="relative w-full h-full flex items-center justify-center"
            >
              <div
                class="absolute w-28 h-28 border border-amber-500/10 rounded-full animate-spin-ultra-slow"
              ></div>
              <div
                class="absolute w-16 h-16 border border-amber-500/20 rounded-full animate-spin-ultra-slow-reverse"
              ></div>
              <div
                class="w-8 h-8 bg-amber-500/10 border border-amber-500/40 rounded-full flex items-center justify-center"
              >
                <div class="w-2 h-2 bg-amber-500/60 rounded-full animate-pulse"></div>
              </div>
            </div>

            <!-- data visual -->
            <div
              v-else-if="project.visual === 'data'"
              class="w-full max-w-[180px] h-20 flex items-end justify-center gap-1.5"
            >
              <div
                class="w-1/6 bg-amber-500/15 rounded-t animate-bar"
                style="height: 30%; animation-delay: 0s"
              ></div>
              <div
                class="w-1/6 bg-amber-500/30 rounded-t animate-bar"
                style="height: 55%; animation-delay: 0.15s"
              ></div>
              <div
                class="w-1/6 bg-amber-500/50 rounded-t animate-bar"
                style="height: 80%; animation-delay: 0.3s"
              ></div>
              <div
                class="w-1/6 bg-amber-500/35 rounded-t animate-bar"
                style="height: 45%; animation-delay: 0.1s"
              ></div>
              <div
                class="w-1/6 bg-amber-500/70 rounded-t animate-bar"
                style="height: 100%; animation-delay: 0.45s"
              ></div>
              <div
                class="w-1/6 bg-amber-500/25 rounded-t animate-bar"
                style="height: 35%; animation-delay: 0.25s"
              ></div>
            </div>

            <!-- ai visual -->
            <div
              v-else-if="project.visual === 'ai'"
              class="relative w-24 h-24 flex items-center justify-center"
            >
              <div
                class="absolute inset-0 border border-amber-500/10 rounded-full animate-ping"
                style="animation-duration: 2s"
              ></div>
              <div
                class="absolute inset-3 border border-amber-500/20 rounded-full animate-ping"
                style="animation-duration: 2.5s; animation-delay: 0.5s"
              ></div>
              <div
                class="w-14 h-14 border border-amber-500/40 rounded-full flex items-center justify-center bg-amber-500/5"
              >
                <span class="text-[10px] font-mono text-amber-500 font-bold">AI</span>
              </div>
            </div>

            <!-- app visual -->
            <div
              v-else-if="project.visual === 'app'"
              class="w-full max-w-[180px] bg-neutral-900 border border-neutral-700/50 rounded-lg p-3 font-mono text-[8px] text-neutral-500"
            >
              <div class="flex gap-1 mb-2">
                <div class="w-2 h-2 rounded-full bg-red-500/40"></div>
                <div class="w-2 h-2 rounded-full bg-yellow-500/40"></div>
                <div class="w-2 h-2 rounded-full bg-green-500/40"></div>
              </div>
              <p><span class="text-amber-500">POST</span> /api/invoice</p>
              <p class="text-green-400/70">→ 200 OK</p>
              <p class="text-neutral-600 mt-1">latency: 42ms</p>
            </div>

            <!-- code visual -->
            <div
              v-else-if="project.visual === 'code'"
              class="w-full max-w-[180px] bg-neutral-900 border border-neutral-700/50 rounded-lg p-3 font-mono text-[8px] text-gray-500"
            >
              <div class="flex gap-1 mb-2">
                <div class="w-2 h-2 rounded-full bg-red-500/40"></div>
                <div class="w-2 h-2 rounded-full bg-yellow-500/40"></div>
                <div class="w-2 h-2 rounded-full bg-green-500/40"></div>
              </div>
              <p>
                <span class="text-amber-500">const</span> ws =
                <span class="text-cyan-400">WebSocket</span>()
              </p>
              <p class="pl-2 text-green-400/70">
                ws.<span class="text-purple-400">emit</span>('sync')
              </p>
              <p class="text-neutral-600">// 10K users</p>
            </div>

            <!-- hover glow -->
            <div
              class="absolute inset-0 bg-gradient-radial from-amber-500/5 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none"
            ></div>
          </div>

          <!-- Card Body -->
          <div class="p-6 flex flex-col flex-grow">
            <!-- Tag -->
            <div class="mb-4">
              <span
                class="text-[9px] font-mono font-bold text-amber-500/60 uppercase tracking-[0.3em] px-2.5 py-1 border border-amber-500/15 rounded-full bg-amber-500/5"
              >
                {{ project.tag }}
              </span>
            </div>

            <!-- Title -->
            <h3
              class="text-xl font-black tracking-tight text-white mb-3 group-hover:text-amber-300 transition-colors duration-400 italic"
            >
              {{ project.title }}
            </h3>

            <!-- Description -->
            <p
              class="text-sm text-gray-400 leading-relaxed font-light mb-5 flex-grow"
              v-html="project.description"
            ></p>

            <!-- Metrics -->
            <div class="flex gap-3 mb-5">
              <div
                v-for="metric in project.metrics"
                :key="metric.label"
                class="flex-1 bg-neutral-900/80 border border-neutral-800/80 rounded-lg p-2.5 text-center group-hover:border-amber-500/15 transition-colors duration-500"
              >
                <p class="text-sm font-black text-amber-400/90 leading-none mb-1">
                  {{ metric.value }}
                </p>
                <p class="text-[8px] font-mono text-neutral-600 uppercase tracking-wider">
                  {{ metric.label }}
                </p>
              </div>
            </div>

            <!-- Footer: tech + actions -->
            <div class="pt-4 border-t border-neutral-800/40 flex items-end justify-between gap-3">
              <!-- Tech tags -->
              <div class="flex flex-wrap gap-1.5">
                <span
                  v-for="tech in project.tech.slice(0, 4)"
                  :key="tech"
                  class="text-[9px] font-mono px-2 py-0.5 border rounded-full transition-all duration-300"
                  :class="getTechColor(tech)"
                >
                  {{ tech }}
                </span>
                <span
                  v-if="project.tech.length > 4"
                  class="text-[9px] font-mono text-neutral-600 px-2 py-0.5"
                >
                  +{{ project.tech.length - 4 }}
                </span>
              </div>

              <!-- GitHub link -->
              <a
                v-if="project.github"
                :href="project.github"
                class="shrink-0 w-7 h-7 rounded-full border border-neutral-700 flex items-center justify-center text-neutral-500 hover:border-amber-500/50 hover:text-amber-500 transition-all duration-300"
                title="View on GitHub"
              >
                <svg class="w-3.5 h-3.5" fill="currentColor" viewBox="0 0 24 24">
                  <path
                    d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"
                  />
                </svg>
              </a>
            </div>
          </div>
        </div>
      </TransitionGroup>

      <!-- Empty state for filter -->
      <div v-if="filteredProjects.length === 0" class="text-center py-24">
        <p class="text-neutral-600 font-mono text-sm">// No projects in this category</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Project Grid Transitions */
.project-grid-move,
.project-grid-enter-active,
.project-grid-leave-active {
  transition: all 0.45s cubic-bezier(0.55, 0, 0.1, 1);
}
.project-grid-enter-from,
.project-grid-leave-to {
  opacity: 0;
  transform: scale(0.94) translateY(10px);
}
.project-grid-leave-active {
  position: absolute;
  width: 100%;
  z-index: 0;
}

/* Orbiting nodes */
@keyframes orbit {
  from {
    transform: rotate(0deg) translateX(var(--orbit-d, 80px)) rotate(0deg);
  }
  to {
    transform: rotate(360deg) translateX(var(--orbit-d, 80px)) rotate(-360deg);
  }
}
.node-orbit {
  animation: orbit 10s linear infinite;
  animation-delay: var(--orbit-delay, 0s);
}

/* Ultra slow spin */
@keyframes spin-ultra-slow {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
.animate-spin-ultra-slow {
  animation: spin-ultra-slow 30s linear infinite;
}
@keyframes spin-ultra-slow-reverse {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(-360deg);
  }
}
.animate-spin-ultra-slow-reverse {
  animation: spin-ultra-slow-reverse 20s linear infinite;
}

/* Pulse slow */
@keyframes pulse-slow {
  0%,
  100% {
    opacity: 0.3;
  }
  50% {
    opacity: 0.8;
  }
}
.animate-pulse-slow {
  animation: pulse-slow 3s ease-in-out infinite;
}

/* Bar chart animation */
@keyframes bar-grow {
  0%,
  100% {
    opacity: 0.5;
    transform: scaleY(1);
  }
  50% {
    opacity: 1;
    transform: scaleY(1.08);
  }
}
.animate-bar {
  animation: bar-grow 2s ease-in-out infinite;
  transform-origin: bottom;
}

/* Radial gradient utility */
.bg-gradient-radial {
  background: radial-gradient(
    circle,
    var(--tw-gradient-from),
    var(--tw-gradient-via),
    var(--tw-gradient-to)
  );
}
</style>
