<script setup lang="ts">
import { ref, onMounted } from 'vue'

const mounted = ref(false)
onMounted(() =>
  setTimeout(() => {
    mounted.value = true
  }, 100),
)

const categories = [
  {
    code: '01',
    label: 'Languages',
    color: 'cyan',
    avgPct: 92,
    skills: [
      { name: 'Python', pct: 96 },
      { name: 'TypeScript', pct: 94 },
      { name: 'SQL', pct: 92 },
      { name: 'C++', pct: 85 },
      { name: 'Java', pct: 84 },
      { name: 'Go', pct: 82 },
    ],
  },
  {
    code: '02',
    label: 'Frontend',
    color: 'lime',
    avgPct: 88,
    skills: [
      { name: 'React / Next.js', pct: 95 },
      { name: 'Angular', pct: 90 },
      { name: 'Tailwind CSS', pct: 94 },
      { name: 'Redux / TanStack', pct: 88 },
      { name: 'Design Systems', pct: 85 },
    ],
  },
  {
    code: '03',
    label: 'Backend',
    color: 'violet',
    avgPct: 91,
    skills: [
      { name: 'Django / FastAPI', pct: 96 },
      { name: 'Node.js (NestJS)', pct: 88 },
      { name: 'GraphQL / gRPC', pct: 86 },
      { name: 'Kafka / Celery', pct: 92 },
      { name: 'Distributed Systems', pct: 94 },
    ],
  },
  {
    code: '04',
    label: 'Databases',
    color: 'sky',
    avgPct: 89,
    skills: [
      { name: 'PostgreSQL', pct: 94 },
      { name: 'DynamoDB / Redis', pct: 92 },
      { name: 'MongoDB / Pinecone', pct: 88 },
      { name: 'Elasticsearch', pct: 82 },
      { name: 'BigQuery / Kafka', pct: 85 },
    ],
  },
  {
    code: '05',
    label: 'DevOps',
    color: 'amber',
    avgPct: 90,
    skills: [
      { name: 'AWS / GCP', pct: 94 },
      { name: 'Docker / K8s', pct: 92 },
      { name: 'Terraform', pct: 88 },
      { name: 'CI/CD (ArgoCD)', pct: 90 },
      { name: 'Prometheus / ELK', pct: 86 },
    ],
  },
  {
    code: '06',
    label: 'AI & ML',
    color: 'orange',
    avgPct: 87,
    skills: [
      { name: 'RAG / LangChain', pct: 94 },
      { name: 'YOLOv5 / Whisper', pct: 92 },
      { name: 'Vector DBs', pct: 90 },
      { name: 'ONNX Runtime', pct: 85 },
      { name: 'Model Evals', pct: 82 },
    ],
  },
]

const palette: Record<string, { r: number; g: number; b: number }> = {
  cyan: { r: 6, g: 182, b: 212 },
  lime: { r: 132, g: 204, b: 22 },
  violet: { r: 139, g: 92, b: 246 },
  sky: { r: 14, g: 165, b: 233 },
  amber: { r: 251, g: 191, b: 36 },
  orange: { r: 251, g: 146, b: 60 },
}
const rgba = (color: string, a: number) => {
  const p = palette[color]
  return `rgba(${p.r},${p.g},${p.b},${a})`
}
const solid: Record<string, string> = {
  cyan: '#22d3ee',
  lime: '#a3e635',
  violet: '#a78bfa',
  sky: '#38bdf8',
  amber: '#fbbf24',
  orange: '#fb923c',
}

// SVG ring: circumference for r=28
const R = 28
const CIRC = 2 * Math.PI * R

const ringOffset = (pct: number) => CIRC * (1 - pct / 100)

const levelLabel = (pct: number) => (pct >= 88 ? 'Expert' : pct >= 72 ? 'Advanced' : 'Proficient')

const hoveredCat = ref<string | null>(null)
</script>

<template>
  <section
    id="skills"
    class="relative min-h-screen bg-black py-24 lg:py-32 overflow-hidden border-b border-neutral-900"
  >
    <!-- Ambient background -->
    <div class="absolute inset-0 z-0 pointer-events-none">
      <div
        class="absolute inset-0 bg-[linear-gradient(to_right,#80808006_1px,transparent_1px),linear-gradient(to_bottom,#80808006_1px,transparent_1px)] bg-[size:40px_40px]"
      ></div>
      <div
        class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[80vw] h-[50vw] rounded-full blur-[180px]"
        style="background: rgba(251, 191, 36, 0.04)"
      ></div>
    </div>

    <div class="max-w-[1440px] mx-auto px-6 lg:px-16 relative z-10 reveal-on-scroll">
      <!-- HUD Header -->
      <div class="mb-14 relative">
        <div class="flex items-center gap-4 mb-3">
          <div class="flex gap-1.5">
            <div
              class="w-1.5 h-1.5 rounded-full bg-green-400 animate-pulse shadow-[0_0_6px_rgba(74,222,128,0.8)]"
            ></div>
            <div
              class="w-1.5 h-1.5 rounded-full bg-amber-400 animate-pulse"
              style="animation-delay: 0.3s"
            ></div>
          </div>
          <span class="text-[9px] font-mono text-amber-500/60 uppercase tracking-[0.5em]"
            >JARVIS // SKILL_MATRIX_v2.0</span
          >
        </div>
        <h2 class="text-xs uppercase tracking-[0.6em] text-amber-500 mb-4 font-bold font-mono">
          Competencies
        </h2>
        <div class="flex flex-col lg:flex-row lg:items-end lg:justify-between gap-4">
          <h1
            class="text-5xl md:text-7xl xl:text-8xl font-black tracking-tighter italic text-white leading-none"
          >
            ENGINEERING<br /><span class="text-neutral-700">ARSENAL</span>
          </h1>
          <p class="text-gray-400 text-sm font-light max-w-xs lg:text-right leading-relaxed">
            <span class="font-mono text-amber-500/80">ANALYSIS COMPLETE</span><br />
            38 modules · 6 domains · all systems nominal.
          </p>
        </div>
        <div class="w-24 h-0.5 bg-gradient-to-r from-amber-500 to-transparent mt-8"></div>
      </div>

      <!-- HUD Panel Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-5">
        <div
          v-for="cat in categories"
          :key="cat.code"
          class="hud-panel group relative overflow-hidden rounded-xl cursor-default"
          :style="{
            borderColor: hoveredCat === cat.label ? rgba(cat.color, 0.5) : rgba(cat.color, 0.18),
            background: `linear-gradient(135deg, rgba(0,0,0,0.95) 0%, ${rgba(cat.color, 0.04)} 100%)`,
            boxShadow:
              hoveredCat === cat.label
                ? `0 0 40px ${rgba(cat.color, 0.15)}, inset 0 0 40px ${rgba(cat.color, 0.04)}`
                : 'none',
          }"
          @mouseenter="hoveredCat = cat.label"
          @mouseleave="hoveredCat = null"
        >
          <!-- Corner brackets -->
          <div class="corner-tl" :style="{ borderColor: solid[cat.color] }"></div>
          <div class="corner-tr" :style="{ borderColor: solid[cat.color] }"></div>
          <div class="corner-bl" :style="{ borderColor: solid[cat.color] }"></div>
          <div class="corner-br" :style="{ borderColor: solid[cat.color] }"></div>

          <!-- Radar sweep -->
          <div
            class="scan-sweep pointer-events-none"
            :style="{
              background: `linear-gradient(to bottom, transparent, ${rgba(cat.color, 0.06)}, transparent)`,
            }"
            :class="hoveredCat === cat.label ? 'scan-fast' : 'scan-slow'"
          ></div>

          <!-- Panel Content -->
          <div class="relative z-10 p-6">
            <!-- Panel Header -->
            <div class="flex items-center gap-4 mb-5">
              <!-- Circular ring -->
              <div class="relative flex-shrink-0">
                <svg :width="R * 2 + 10" :height="R * 2 + 10" class="transform -rotate-90">
                  <!-- Track -->
                  <circle
                    :cx="R + 5"
                    :cy="R + 5"
                    :r="R"
                    fill="none"
                    :stroke="rgba(cat.color, 0.12)"
                    stroke-width="3"
                  />
                  <!-- Progress -->
                  <circle
                    :cx="R + 5"
                    :cy="R + 5"
                    :r="R"
                    fill="none"
                    :stroke="solid[cat.color]"
                    stroke-width="3"
                    stroke-linecap="round"
                    :stroke-dasharray="CIRC"
                    :stroke-dashoffset="mounted ? ringOffset(cat.avgPct) : CIRC"
                    style="transition: stroke-dashoffset 1.2s cubic-bezier(0.4, 0, 0.2, 1)"
                    :style="{ filter: `drop-shadow(0 0 4px ${solid[cat.color]})` }"
                  />
                </svg>
                <!-- Center % -->
                <div class="absolute inset-0 flex items-center justify-center">
                  <span
                    class="text-[11px] font-mono font-black"
                    :style="{ color: solid[cat.color] }"
                  >
                    {{ cat.avgPct }}%
                  </span>
                </div>
              </div>

              <!-- Category name -->
              <div class="flex-grow min-w-0">
                <div class="flex items-center gap-2 mb-1">
                  <span
                    class="text-[8px] font-mono uppercase tracking-[0.4em]"
                    :style="{ color: rgba(cat.color, 0.6) }"
                  >
                    {{ cat.code }} / MODULE
                  </span>
                </div>
                <h3
                  class="text-base font-black uppercase tracking-tight leading-none"
                  :style="{ color: solid[cat.color] }"
                >
                  {{ cat.label }}
                </h3>
                <p class="text-[8px] font-mono text-neutral-600 mt-1 uppercase tracking-widest">
                  {{ cat.skills.length }} skills loaded
                </p>
              </div>
            </div>

            <!-- Divider -->
            <div
              class="h-px mb-4"
              :style="{
                background: `linear-gradient(to right, ${rgba(cat.color, 0.4)}, transparent)`,
              }"
            ></div>

            <!-- Skills -->
            <div class="space-y-2.5">
              <div v-for="skill in cat.skills" :key="skill.name" class="skill-row group/skill">
                <div class="flex items-center justify-between mb-1">
                  <span
                    class="text-[10px] font-mono text-neutral-300 uppercase tracking-wider group-hover/skill:text-white transition-colors"
                  >
                    {{ skill.name }}
                  </span>
                  <span
                    class="text-[8px] font-mono tracking-widest"
                    :style="{ color: rgba(cat.color, 0.7) }"
                  >
                    {{ levelLabel(skill.pct) }}
                  </span>
                </div>
                <!-- Bar track -->
                <div
                  class="h-1 rounded-full overflow-hidden"
                  :style="{ background: rgba(cat.color, 0.1) }"
                >
                  <div
                    class="h-full rounded-full transition-all duration-1000 ease-out"
                    :style="{
                      width: mounted ? skill.pct + '%' : '0%',
                      background: `linear-gradient(to right, ${rgba(cat.color, 0.6)}, ${solid[cat.color]})`,
                      boxShadow: `0 0 6px ${rgba(cat.color, 0.4)}`,
                    }"
                  ></div>
                </div>
              </div>
            </div>

            <!-- Bottom status line -->
            <div
              class="mt-5 pt-3 flex items-center justify-between"
              :style="{ borderTop: `1px solid ${rgba(cat.color, 0.1)}` }"
            >
              <span
                class="text-[7px] font-mono uppercase tracking-[0.3em]"
                :style="{ color: rgba(cat.color, 0.35) }"
              >
                SYS_MODULE_ACTIVE
              </span>
              <div class="flex gap-1">
                <div
                  v-for="i in 3"
                  :key="i"
                  class="w-1 h-1 rounded-full"
                  :style="{ background: rgba(cat.color, i === 1 ? 0.8 : 0.2) }"
                ></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Panel border */
.hud-panel {
  border: 1px solid;
  transition:
    border-color 0.4s ease,
    box-shadow 0.4s ease;
}

/* Corner brackets */
.corner-tl,
.corner-tr,
.corner-bl,
.corner-br {
  position: absolute;
  width: 14px;
  height: 14px;
  z-index: 20;
  border-style: solid;
  border-color: inherit;
  transition: all 0.4s ease;
}
.corner-tl {
  top: -1px;
  left: -1px;
  border-width: 2px 0 0 2px;
}
.corner-tr {
  top: -1px;
  right: -1px;
  border-width: 2px 2px 0 0;
}
.corner-bl {
  bottom: -1px;
  left: -1px;
  border-width: 0 0 2px 2px;
}
.corner-br {
  bottom: -1px;
  right: -1px;
  border-width: 0 2px 2px 0;
}

/* Group hover: expand brackets */
.group:hover .corner-tl,
.group:hover .corner-bl {
  width: 20px;
  height: 20px;
}
.group:hover .corner-tr,
.group:hover .corner-br {
  width: 20px;
  height: 20px;
}

/* Radar sweep animation */
.scan-sweep {
  position: absolute;
  inset: 0;
  pointer-events: none;
  background-size: 100% 40%;
  background-repeat: no-repeat;
}

@keyframes sweep-slow {
  0% {
    background-position: 0 -40%;
  }
  100% {
    background-position: 0 140%;
  }
}
@keyframes sweep-fast {
  0% {
    background-position: 0 -40%;
  }
  100% {
    background-position: 0 140%;
  }
}
.scan-slow {
  animation: sweep-slow 4s linear infinite;
}
.scan-fast {
  animation: sweep-fast 1.8s linear infinite;
}
</style>
