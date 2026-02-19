<script setup lang="ts">
import { reactive, ref, onMounted, onBeforeUnmount } from 'vue'

const containerRef = ref<HTMLElement | null>(null)
const hubRef = ref<HTMLElement | null>(null)
const nodeRefs = ref<(HTMLElement | null)[]>([])
const hubCoords = reactive({ x: 0, y: 0 })
const nodeCoords = reactive<Array<{ x: number; y: number }>>([])

const nodes = [
  {
    title: 'Languages',
    pos: 'top-0 left-0 lg:left-[5%]',
    skills: ['Python', 'TypeScript', 'Go', 'Java', 'SQL'],
  },
  {
    title: 'Cloud_&_DevOps',
    pos: 'top-0 right-0 lg:right-[5%]',
    skills: ['AWS (ECS/Lambda)', 'Docker & K8s', 'Terraform', 'CI/CD', 'Linux'],
  },
  {
    title: 'Frontend',
    pos: 'top-[32%] lg:top-1/2 lg:-translate-y-1/2 left-0 lg:-left-[5%]',
    skills: ['React', 'Angular', 'Tailwind', 'Next.js', 'Redux'],
  },
  {
    title: 'Backend_Systems',
    pos: 'top-[32%] lg:top-1/2 lg:-translate-y-1/2 right-0 lg:-right-[5%]',
    skills: ['Django', 'Node.js', 'FastAPI', 'gRPC', 'GraphQL'],
  },
  {
    title: 'Data_&_Distributed',
    pos: 'bottom-0 left-0 lg:left-[5%]',
    skills: ['Kafka', 'Redis', 'PostgreSQL', 'MongoDB', 'Elasticsearch'],
  },
  {
    title: 'Tools_&_Methods',
    pos: 'bottom-0 right-0 lg:right-[5%]',
    skills: ['Prometheus', 'Grafana', 'Git', 'Agile', 'System Design'],
  },
]

const isHTMLElement = (el: unknown): el is HTMLElement => {
  return el instanceof HTMLElement
}

const updateCoords = () => {
  if (!containerRef.value || !hubRef.value) return
  const rootRect = containerRef.value.getBoundingClientRect()

  // Update Hub Center
  const hRect = hubRef.value.getBoundingClientRect()
  hubCoords.x = hRect.left + hRect.width / 2 - rootRect.left
  hubCoords.y = hRect.top + hRect.height / 2 - rootRect.top

  // Update Node Centers
  nodeRefs.value.forEach((el, i) => {
    if (el && isHTMLElement(el)) {
      const nRect = el.getBoundingClientRect()
      nodeCoords[i] = {
        x: nRect.left + nRect.width / 2 - rootRect.left,
        y: nRect.top + nRect.height / 2 - rootRect.top,
      }
    }
  })
}

let observer: ResizeObserver | null = null
onMounted(() => {
  updateCoords()
  observer = new ResizeObserver(updateCoords)
  if (containerRef.value) {
    observer.observe(containerRef.value)
  }
  window.addEventListener('scroll', updateCoords)
})

onBeforeUnmount(() => {
  observer?.disconnect()
  window.removeEventListener('scroll', updateCoords)
})
</script>

<template>
  <section id="skills" class="min-h-screen bg-black py-20 lg:py-32 relative overflow-hidden">
    <div class="relative z-10 reveal-on-scroll">
      <div
        class="w-full max-w-[1440px] mx-auto min-h-screen bg-black text-white p-6 lg:px-16 relative"
        ref="containerRef"
      >
        <svg class="hidden lg:block absolute inset-0 z-0 pointer-events-none w-full h-full">
          <defs>
            <filter id="glow">
              <feGaussianBlur stdDeviation="2.5" result="coloredBlur" />
              <feMerge>
                <feMergeNode in="coloredBlur" />
                <feMergeNode in="SourceGraphic" />
              </feMerge>
            </filter>
            <radialGradient id="packetGlow">
              <stop offset="0%" stop-color="#fbbf24" />
              <stop offset="100%" stop-color="transparent" />
            </radialGradient>
          </defs>

          <g v-for="(node, i) in nodes" :key="'link-' + i">
            <line
              :x1="hubCoords.x"
              :y1="hubCoords.y"
              :x2="nodeCoords[i]?.x"
              :y2="nodeCoords[i]?.y"
              stroke="#fbbf24"
              stroke-width="1"
              stroke-dasharray="4 8"
              opacity="0.2"
            />
            <circle r="3" fill="url(#packetGlow)" filter="url(#glow)">
              <animateMotion
                :path="`M ${hubCoords.x},${hubCoords.y} L ${nodeCoords[i]?.x},${nodeCoords[i]?.y}`"
                :dur="`${2 + Math.random() * 2}s`"
                repeatCount="indefinite"
              />
            </circle>
          </g>
        </svg>

        <div class="relative z-10 text-center mb-16 lg:mb-32">
          <h2 class="text-xs uppercase tracking-[0.6em] text-amber-500 mb-4 font-bold">
            Competencies
          </h2>
          <h1 class="text-4xl md:text-7xl font-black italic uppercase tracking-tighter">
            Engineering <span class="text-neutral-800">Arsenal</span>
          </h1>
          <div class="w-16 h-1 bg-amber-500 mx-auto mt-6 rounded-full"></div>
        </div>

        <div class="relative flex flex-col items-center gap-6 lg:block w-full h-auto lg:h-[800px]">
          <!-- Central Hub -->
          <div
            ref="hubRef"
            class="hidden lg:flex absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 z-30 w-48 h-48 rounded-full border border-amber-500/50 bg-black/80 backdrop-blur-md flex-col items-center justify-center p-4 shadow-[0_0_80px_rgba(251,191,36,0.1)] animate-pulse-slow"
          >
            <div
              class="absolute inset-0 border border-amber-500/20 rounded-full animate-spin-slow"
            ></div>
            <h3 class="text-xl font-black text-center leading-none tracking-tight">
              CORE<br /><span class="text-amber-500">GATEWAY</span>
            </h3>
            <p class="text-[8px] font-mono text-gray-500 mt-2 uppercase tracking-widest">
              Stack Architecture
            </p>
          </div>

          <!-- Nodes -->
          <div
            v-for="(node, index) in nodes"
            :key="index"
            :ref="
              (el) => {
                if (isHTMLElement(el)) {
                  nodeRefs[index] = el
                }
              }
            "
            :class="[
              'w-full max-w-sm lg:absolute lg:w-72 bg-neutral-900/20 backdrop-blur-xl border border-neutral-800 p-6 rounded-xl hover:border-amber-500/40 hover:bg-neutral-900/60 transition-all duration-500 z-20 group',
              node.pos,
            ]"
          >
            <div class="flex items-center gap-3 mb-4 border-b border-neutral-800/50 pb-3">
              <div
                class="w-1.5 h-1.5 bg-amber-500 rounded-full animate-pulse group-hover:scale-150 transition-transform shadow-[0_0_10px_rgba(251,191,36,0.5)]"
              ></div>
              <h4 class="text-[10px] font-mono font-black uppercase text-amber-500 tracking-widest">
                {{ node.title.replace('_', ' ') }}
              </h4>
            </div>
            <ul class="grid grid-cols-2 lg:grid-cols-1 gap-y-2 lg:gap-y-2">
              <li
                v-for="skill in node.skills"
                :key="skill"
                class="flex items-center justify-between text-xs text-neutral-400 group-hover:text-white transition-colors"
              >
                <span>{{ skill }}</span>
                <div
                  class="hidden lg:block w-1 h-1 bg-neutral-800 rounded-full group-hover:bg-amber-500 transition-colors"
                ></div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@keyframes spin-slow {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
.animate-spin-slow {
  animation: spin-slow 20s linear infinite;
}

@keyframes pulse-slow {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.8;
  }
}
.animate-pulse-slow {
  animation: pulse-slow 4s ease-in-out infinite;
}
</style>
