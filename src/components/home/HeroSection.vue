<script setup lang="ts">
import { ref, onMounted } from 'vue'

const roles = ['Software Engineer', 'Full-Stack Specialist', 'AI/ML Builder', 'Problem Solver']
const currentRole = ref('')
let roleIndex = 0
let charIndex = 0
let isDeleting = false

const typeEffect = () => {
  const fullText = roles[roleIndex]
  if (!fullText) return
  isDeleting ? charIndex-- : charIndex++
  currentRole.value = fullText.substring(0, charIndex)

  let speed = isDeleting ? 40 : 120
  if (!isDeleting && charIndex === fullText.length) {
    isDeleting = true
    speed = 2500
  } else if (isDeleting && charIndex === 0) {
    isDeleting = false
    roleIndex = (roleIndex + 1) % roles.length
    speed = 500
  }
  setTimeout(typeEffect, speed)
}

onMounted(() => {
  typeEffect()
})
</script>

<template>
  <section
    id="home"
    class="snap-start min-h-screen relative flex items-center justify-center border-b border-neutral-900 bg-black overflow-hidden"
  >
    <!-- Background Elements -->
    <div class="absolute inset-0 z-0">
      <div
        class="absolute inset-0 bg-[linear-gradient(to_right,#80808012_1px,transparent_1px),linear-gradient(to_bottom,#80808012_1px,transparent_1px)] bg-[size:40px_40px]"
      ></div>
      <div
        class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[60vw] h-[60vw] bg-amber-500/5 rounded-full blur-[120px] animate-pulse-slow"
      ></div>
    </div>

    <!-- Main Content Container -->
    <div class="max-w-[1600px] mx-auto px-6 lg:px-24 z-10 reveal-on-scroll w-full">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-24 items-center">
        <div
          class="space-y-8 lg:space-y-10 mt-20 lg:mt-0 text-center lg:text-left flex flex-col items-center lg:items-start"
        >
          <div class="space-y-4">
            <h3
              class="text-white text-lg lg:text-2xl xl:text-3xl font-extralight tracking-widest opacity-60 uppercase"
            >
              INIT_HANDSHAKE // 👋
            </h3>

            <h1
              class="text-5xl md:text-7xl lg:text-8xl xl:text-9xl font-black italic uppercase tracking-tighter leading-[0.9] text-white"
            >
              Subrahmanyam <br />
              <span class="breathing-color">Konakanchi</span>
            </h1>

            <div
              class="flex items-center gap-4 lg:gap-6 h-12 w-full justify-center lg:justify-start"
            >
              <div class="hidden sm:block h-px w-12 lg:w-16 bg-neutral-800"></div>
              <span
                class="text-lg lg:text-2xl font-mono text-neutral-400 uppercase tracking-[0.2em] lg:tracking-[0.3em]"
              >
                {{ currentRole }}<span class="animate-blink">_</span>
              </span>
            </div>
          </div>

          <p
            class="text-gray-400 text-lg xl:text-xl max-w-lg xl:max-w-xl leading-relaxed font-light"
          >
            A <span class="text-white font-medium">curious builder</span> and Software Engineer 
            from the <span class="text-amber-500 italic">University of Florida</span>. I
            specialize in bridging the gap between crisp interfaces and robust backend logic to make
            life <span class="italic">meaningfully better</span>.
          </p>

          <div class="flex flex-col sm:flex-row gap-6 sm:gap-8 pt-6 w-full sm:w-auto">
            <a
              href="#projects"
              class="group relative inline-flex justify-center px-10 py-5 text-black bg-amber-500 font-black uppercase tracking-widest overflow-hidden transition-all duration-500"
            >
              <span class="relative z-10">View Projects</span>
              <div
                class="absolute inset-0 bg-white translate-y-full group-hover:translate-y-0 transition-transform duration-300"
              ></div>
            </a>
            <a
              href="/resume.pdf"
              target="_blank"
              class="inline-flex justify-center px-10 py-5 border border-neutral-800 text-neutral-500 font-bold uppercase tracking-widest hover:text-white hover:border-amber-500 transition-all font-mono"
            >
              Resume.exe
            </a>
          </div>
        </div>

        <div class="relative flex justify-center items-center py-6 lg:py-0 mt-8 lg:mt-0">
          <div
            class="absolute inset-0 border border-amber-500/10 rounded-full animate-orbit-slow scale-150"
          ></div>

          <div class="relative z-10">
            <div class="relative overflow-hidden rounded-3xl">
              <img
                src="@/assets/Man.png"
                class="max-h-[50vh] lg:max-h-[75vh] xl:max-h-[80vh] w-auto object-contain drop-shadow-[0_0_50px_rgba(251,191,36,0.1)] transition-all duration-1000 ease-in-out breathing-image"
                alt="Subrahmanyam Konakanchi"
              />
            </div>

            <div
              class="absolute -bottom-6 -right-6 lg:-right-12 bg-neutral-900/80 border border-neutral-800 p-5 rounded-2xl shadow-2xl backdrop-blur-xl"
            >
              <p
                class="text-[9px] font-mono text-amber-500 uppercase font-bold mb-2 tracking-widest"
              >
                Human_Location
              </p>
              <p class="text-sm font-bold text-white italic">Nashville, TN</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Scoped animations needed for Hero Section */
@keyframes color-breathe {
  0%,
  100% {
    color: #fbbf24;
    filter: drop-shadow(0 0 0px rgba(251, 191, 36, 0));
  }
  50% {
    color: #ffffff;
    filter: drop-shadow(0 0 15px rgba(251, 191, 36, 0.4));
  }
}
.breathing-color {
  animation: color-breathe 4s ease-in-out infinite;
}

@keyframes image-breathe {
  0%,
  100% {
    filter: grayscale(100%) brightness(0.7);
    opacity: 0.8;
  }
  50% {
    filter: grayscale(0%) brightness(1.1);
    opacity: 1;
  }
}
.breathing-image {
  animation: image-breathe 4s ease-in-out infinite;
}

@keyframes pulse-slow {
  0%,
  100% {
    opacity: 0.05;
    transform: translate(-50%, -50%) scale(1);
  }
  50% {
    opacity: 0.15;
    transform: translate(-50%, -50%) scale(1.1);
  }
}
.animate-pulse-slow {
  animation: pulse-slow 8s ease-in-out infinite;
}

@keyframes orbit-slow {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
.animate-orbit-slow {
  animation: orbit-slow 40s linear infinite;
}

@keyframes blink {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
}
.animate-blink {
  animation: blink 1s infinite;
}

.bg-grid-large {
  background-image:
    linear-gradient(to right, #80808012 1px, transparent 1px),
    linear-gradient(to bottom, #80808012 1px, transparent 1px);
  background-size: 50px 50px;
}
</style>
