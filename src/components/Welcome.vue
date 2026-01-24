<script setup>
import { ref, onMounted } from 'vue'

import gatorsLogo from '@/assets/florida_gators.jpg'
import srm from '@/assets/srm.jpg'

// Separate refs for better control over animation timing
const eduExpanded = ref([])
const workExpanded = ref({})
const isLoaded = ref(false)

import { reactive, onBeforeUnmount } from 'vue'

const containerRef = ref(null)
const hubRef = ref(null)
const nodeRefs = ref([])
const hubCoords = reactive({ x: 0, y: 0 })
const nodeCoords = reactive([])

const socialLinks = [
  { name: 'LinkedIn', url: '#' },
  { name: 'GitHub', url: '#' },
  { name: 'Portfolio', url: '#' },
]

const nodes = [
  {
    title: 'Programming_Languages',
    pos: 'top-0 left-0 lg:left-[5%]',
    skills: ['Python', 'Java', 'C++', 'JavaScript', 'TypeScript'],
  },
  {
    title: 'Infrastructure_&_Cloud',
    pos: 'top-0 right-0 lg:right-[5%]',
    skills: ['AWS', 'Docker', 'Jenkins', 'GitHub Actions', 'CI/CD', 'Git'],
  },
  {
    title: 'Frontend_Technologies',
    pos: 'top-[32%] lg:top-1/2 lg:-translate-y-1/2 left-0 lg:-left-[5%]',
    skills: ['React', 'Angular', 'Tailwind CSS', 'HTML'],
  },
  {
    title: 'Backend_Systems',
    pos: 'top-[32%] lg:top-1/2 lg:-translate-y-1/2 right-0 lg:-right-[5%]',
    skills: ['Django', 'Node.js', 'REST & GraphQL', 'Microservices', 'Kafka'],
  },
  {
    title: 'Database_Architecture',
    pos: 'bottom-0 left-0 lg:left-[5%]',
    skills: ['MySQL', 'PostgreSQL', 'MongoDB', 'DynamoDB', 'Redis'],
  },
  {
    title: 'Quality_&_SDLC',
    pos: 'bottom-0 right-0 lg:right-[5%]',
    skills: ['Celery', 'JIRA', 'Agile/Scrum', 'Playwright', 'Selenium', 'TDD'],
  },
]

const updateCoords = () => {
  if (!containerRef.value || !hubRef.value) return
  const rootRect = containerRef.value.getBoundingClientRect()

  // Update Hub Center
  const hRect = hubRef.value.getBoundingClientRect()
  hubCoords.x = hRect.left + hRect.width / 2 - rootRect.left
  hubCoords.y = hRect.top + hRect.height / 2 - rootRect.top

  // Update Node Centers
  nodeRefs.value.forEach((el, i) => {
    if (el) {
      const nRect = el.getBoundingClientRect()
      nodeCoords[i] = {
        x: nRect.left + nRect.width / 2 - rootRect.left,
        y: nRect.top + nRect.height / 2 - rootRect.top,
      }
    }
  })
}

let observer
onMounted(() => {
  updateCoords()
  observer = new ResizeObserver(updateCoords)
  observer.observe(containerRef.value)
  window.addEventListener('scroll', updateCoords)
})

onBeforeUnmount(() => {
  observer?.disconnect()
  window.removeEventListener('scroll', updateCoords)
  window.removeEventListener('scroll', updateCoords) // Cleanup scroll listener
})
const services = [
  {
    id: 'Compute_Engine',
    pos: 'top-0 left-0',
    cablePos: 'bottom-[-40px] right-[-100px] rotate-[35deg]',
    cableWidth: '150px',
    stack: ['Python / Django', 'Go / gRPC', 'Rust (WASM)', 'Node.js'],
  },
  {
    id: 'Data_Persistence',
    pos: 'top-0 right-0',
    cablePos: 'bottom-[-40px] left-[-100px] rotate-[-35deg]',
    cableWidth: '150px',
    stack: ['PostgreSQL', 'Redis / Kafka', 'AWS DynamoDB', 'S3 Storage'],
  },
  {
    id: 'Neural_Inference',
    pos: 'bottom-0 left-0',
    cablePos: 'top-[-40px] right-[-100px] rotate-[-35deg]',
    cableWidth: '150px',
    stack: ['YOLOv5 / CV', 'Transformers', 'Whisper AI', 'spaCy'],
  },
  {
    id: 'Cloud_Ops',
    pos: 'bottom-0 right-0',
    cablePos: 'top-[-40px] left-[-100px] rotate-[35deg]',
    cableWidth: '150px',
    stack: ['AWS ECS Fargate', 'Kubernetes', 'Docker', 'Terraform'],
  },
]

const systemModules = [
  {
    id: 'RUNTIME_LANGUAGES',
    items: [
      { name: 'Python', status: 'OPTIMIZED', score: 95 },
      { name: 'Go', status: 'STABLE', score: 85 },
      { name: 'Rust', status: 'EXPERIMENTAL', score: 65 },
      { name: 'TypeScript', status: 'STABLE', score: 90 },
    ],
  },
  {
    id: 'DATA_ARCHITECTURE',
    items: [
      { name: 'PostgreSQL', status: 'SCALED', score: 95 },
      { name: 'Redis', status: 'LOCKED', score: 85 },
      { name: 'AWS S3/RDS', status: 'PROVISIONED', score: 90 },
      { name: 'Kafka', status: 'BUFFERED', score: 80 },
    ],
  },
  {
    id: 'ML_COMPUTER_VISION',
    items: [
      { name: 'YOLOv5/OpenCV', status: 'INFERENCE_READY', score: 95 },
      { name: 'PyTorch', status: 'TRAINED', score: 80 },
      { name: 'Whisper AI', status: 'ACTIVE', score: 85 },
      { name: 'D3.js Viz', status: 'RENDERED', score: 90 },
    ],
  },
]

const tools = [
  'DOCKER',
  'KUBERNETES',
  'TERRAFORM',
  'LINUX_KERNEL',
  'GIT_ACTIONS',
  'PROMETHEUS',
  'GRPC',
]

const skillStack = [
  {
    title: 'Backend & Systems',
    skills: [
      { name: 'Python / Django', level: 'Expert', width: '95%' },
      { name: 'Go / gRPC', level: 'Advanced', width: '85%' },
      { name: 'Node.js', level: 'Intermediate', width: '70%' },
      { name: 'PostgreSQL', level: 'Expert', width: '90%' },
    ],
  },
  {
    title: 'Frontend Engineering',
    skills: [
      { name: 'Angular / SSR', level: 'Expert', width: '92%' },
      { name: 'React', level: 'Advanced', width: '88%' },
      { name: 'D3.js / Tailwind', level: 'Expert', width: '90%' },
      { name: 'TypeScript', level: 'Advanced', width: '85%' },
    ],
  },
  {
    title: 'Cloud & Devops',
    skills: [
      { name: 'AWS (ECS/Lambda)', level: 'Expert', width: '94%' },
      { name: 'Kubernetes / Docker', level: 'Advanced', width: '82%' },
      { name: 'Prometheus / Grafana', level: 'Advanced', width: '80%' },
      { name: 'Terraform', level: 'Intermediate', width: '65%' },
    ],
  },
  {
    title: 'AI & Data Science',
    skills: [
      { name: 'Computer Vision', level: 'Expert', width: '90%' },
      { name: 'NLP / Transformers', level: 'Advanced', width: '85%' },
      { name: 'PyTorch / YOLOv5', level: 'Advanced', width: '80%' },
      { name: 'Big Data Rendering', level: 'Expert', width: '92%' },
    ],
  },
]

// const tools = [
//   'Git / GitHub Actions',
//   'Redis',
//   'Kafka',
//   'Linux',
//   'Microservices',
//   'Unit Testing',
//   'Agile / Scrum',
// ]

const educationHistory = [
  {
    university: 'University of Florida',
    location: 'Gainesville, FL',
    period: 'August 2023 - May 2025',
    degree: 'MS in Computer and Information Science Engineering',
    cgpa: '3.90 / 4.00',
    image: gatorsLogo,
  },
  {
    university: 'SRM University',
    location: 'Amaravati, AP',
    period: 'June 2019 - May 2023',
    degree: 'Bachelors in Computer Science Engineering',
    cgpa: '3.81 / 4.00',
    image: srm,
  },
]

const workHistory = [
  {
    company: 'Scholarship Auditions',
    role: 'Software Engineer',
    location: 'Nashville, TN',
    period: 'Oct 2024 – Present',
    bullets: [
      'Spearheaded migration of legacy Webflow/Angular MVP into a <strong>unified Django & Angular ecosystem</strong>, implementing SSR to boost SEO and cut load times by 65%.',
      'Engineered an elastic, <strong>cost-optimized AWS microservice architecture</strong> (ECS Fargate) handling up to 100K requests/day with Prometheus and Grafana.',
      'Designed a <strong>serverless bulk upload system</strong> (S3, Lambda, SQS) to securely onboard 40,000+ students at once without application downtime.',
    ],
  },
  {
    company: 'Avairsense',
    role: 'Backend Engineer',
    location: 'Bangalore, India',
    period: 'Nov 2021 – Feb 2022',
    bullets: [
      'Engineered high-throughput <strong>CV pipeline (Python, OpenCV, YOLOv5)</strong> leveraging multi-threading to process 50+ concurrent video streams.',
      'Achieved sub-200ms inference latency and optimized cloud compute costs by 25% by re-configuring memory bottlenecks.',
      'Profiled resource consumption to optimize data ingestion flows across high-memory processing tasks.',
    ],
  },
  {
    company: 'LegalBill Pro',
    role: 'Freelance Software Engineer',
    location: 'Remote (WA Law Firm)',
    period: 'Project Based',
    bullets: [
      'Designed a full-stack billing platform (React/AWS Serverless) integrating <strong>Microsoft Teams API</strong> and PostgreSQL for transactional records.',
      'Automated client payment lifecycle for 12,000+ annual invoices, reducing average collection time from 45 to 14 days.',
      'Engineered a secure document tracking service in <strong>Python/Django</strong> with version control and user history logging.',
    ],
  },
]

const hackathons = [
  {
    title: 'HackVerse 3.0',
    issuer: 'NIT Rourkela',
    award: 'Best AI/ML Application',
    date: '2023',
    tags: ['NLP', 'Transformers', 'Python', 'Whisper'],
    description:
      'Developed <strong>Quantify</strong>, an AI translation platform utilizing <strong>Helsinki-NLP Transformer models</strong>. Implemented <strong>Whisper</strong> for speech-to-text and <strong>spaCy</strong> for document classification.',
  },
  {
    title: 'Ingenious Hackathon',
    issuer: 'Ahmedabad University',
    award: 'Winner: Distributed Systems Category',
    date: '2023',
    tags: ['Go', 'gRPC', 'Redis', 'Kafka', 'K8s'],
    description:
      'Architected <strong>NexusMesh</strong>, a distributed event-driven mesh network designed for ultra-low latency state synchronization. Utilized <strong>gRPC</strong> for service communication and <strong>Kafka</strong> for handling asynchronous event streams, ensuring consistent state across 1,000+ simulated nodes.',
  },
  {
    title: 'Hack SRM 3.0',
    issuer: 'SRM University AP',
    award: 'Overall Grand Winner',
    date: '2022',
    tags: ['Rust', 'WebAssembly', 'WebRTC', 'PostgreSQL'],
    description:
      'Engineered <strong>EtherSync</strong>, a decentralized peer-to-peer collaborative workspace. Optimized real-time data conflict resolution using <strong>CRDTs</strong> and leveraged <strong>WebAssembly</strong> to perform heavy computations in the browser, reducing server-side overhead by 80%.',
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

const roles = ['Software Engineer', 'Full-Stack Specialist', 'Curious Builder', 'Problem Solver']
const currentRole = ref('')
let roleIndex = 0
let charIndex = 0
let isDeleting = false

const typeEffect = () => {
  const fullText = roles[roleIndex]
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

const initScrollObserver = () => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        // When a section enters the view, add the 'is-visible' class
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible')
        }
      })
    },
    { threshold: 0.15 },
  ) // Trigger when 15% of section is visible

  document.querySelectorAll('.reveal-on-scroll').forEach((el) => observer.observe(el))
}

const toggleWork = (index) => {
  workExpanded.value[index] = !workExpanded.value[index]
}

onMounted(async () => {
  // Initialize your expansion arrays
  eduExpanded.value = educationHistory.map(() => false)
  workExpanded.value = workHistory.map(() => false)

  typeEffect() // Start typewriter
  initScrollObserver() // Start scroll reveals

  await nextTick() // Wait for DOM to be ready
  updateCoords() // Initial mesh calculation

  window.addEventListener('scroll', updateCoords)

  // Trigger timeline animations
  setTimeout(() => {
    eduExpanded.value = educationHistory.map(() => true)

    // For work history, we set each index to true to slide them open initially
    workHistory.forEach((_, index) => {
      workExpanded.value[index] = true
    })
  }, 400)
})
</script>

<style scoped>
/* Color Breath for Konakanchi */
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
  display: inline-block;
  animation: color-breathe 4s ease-in-out infinite;
}

/* Color Breath for Image (using saturation and brightness) */
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

/* Background pulse */
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

.animate-blink {
  animation: blink 1s infinite;
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

.reveal-on-scroll {
  opacity: 0;
  transform: translateY(30px);
  transition: all 1s cubic-bezier(0.22, 1, 0.36, 1);
}

.reveal-on-scroll.is-visible {
  opacity: 1;
  transform: translateY(0);
}

/* SECTION TEXTURES */
.bg-grid-large {
  background-image:
    linear-gradient(to right, #80808012 1px, transparent 1px),
    linear-gradient(to bottom, #80808012 1px, transparent 1px);
  background-size: 50px 50px;
}

.bg-terminal-lines {
  background:
    linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%),
    linear-gradient(90deg, rgba(251, 191, 36, 0.02), rgba(251, 191, 36, 0.01));
  background-size:
    100% 4px,
    2px 100%;
}

.bg-dot-matrix {
  background-image: radial-gradient(rgba(251, 191, 36, 0.08) 1px, transparent 1px);
  background-size: 20px 20px;
}

.bg-circuit-pattern {
  background-image: radial-gradient(rgba(255, 255, 255, 0.03) 1px, transparent 1px);
  background-size: 40px 40px;
}

.reveal-on-scroll {
  opacity: 0;
  transform: translateY(30px);
  transition: all 1s cubic-bezier(0.22, 1, 0.36, 1);
}

.reveal-on-scroll.is-visible {
  opacity: 1;
  transform: translateY(0);
}
</style>

<template>
  <section
    id="home"
    class="snap-start min-h-screen relative flex items-center border-b border-neutral-900 bg-grid-large"
  >
    <div class="container mx-auto px-6 lg:px-24 z-10 reveal-on-scroll">
      <div class="relative min-h-screen bg-black overflow-hidden flex items-center font-sans">
        <div class="absolute inset-0 z-0">
          <div
            class="absolute inset-0 bg-[linear-gradient(to_right,#80808012_1px,transparent_1px),linear-gradient(to_bottom,#80808012_1px,transparent_1px)] bg-[size:40px_40px]"
          ></div>
          <div
            class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[60vw] h-[60vw] bg-amber-500/5 rounded-full blur-[120px] animate-pulse-slow"
          ></div>
        </div>

        <div class="container mx-auto px-6 lg:px-24 z-10">
          <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 lg:gap-24 items-center">
            <div class="space-y-10">
              <div class="space-y-4">
                <h3
                  class="text-white text-2xl lg:text-3xl font-extralight tracking-widest opacity-60"
                >
                  INIT_HANDSHAKE // 👋
                </h3>

                <h1
                  class="text-6xl lg:text-8xl font-black italic uppercase tracking-tighter leading-none text-white"
                >
                  Subrahmanyam <br />
                  <span class="breathing-color">Konakanchi</span>
                </h1>

                <div class="flex items-center gap-6 h-12">
                  <div class="h-[1px] w-16 bg-neutral-800"></div>
                  <span
                    class="text-xl lg:text-2xl font-mono text-neutral-400 uppercase tracking-[0.3em]"
                  >
                    {{ currentRole }}<span class="animate-blink">_</span>
                  </span>
                </div>
              </div>

              <p class="text-gray-400 text-lg max-w-lg leading-relaxed font-light">
                A <span class="text-white font-medium">curious builder</span> and Computer Science
                graduate from the <span class="text-amber-500 italic">University of Florida</span>.
                I specialize in bridging the gap between crisp interfaces and robust backend logic
                to make life <span class="italic">meaningfully better</span>.
              </p>

              <div class="flex gap-8 pt-6">
                <button
                  class="group relative px-8 py-4 text-black bg-amber-500 font-black uppercase tracking-widest overflow-hidden transition-all duration-500"
                >
                  <span class="relative z-10">View Projects</span>
                  <div
                    class="absolute inset-0 bg-white translate-y-full group-hover:translate-y-0 transition-transform duration-300"
                  ></div>
                </button>
                <button
                  class="px-8 py-4 border border-neutral-800 text-neutral-500 font-bold uppercase tracking-widest hover:text-white hover:border-amber-500 transition-all"
                >
                  Resume.exe
                </button>
              </div>
            </div>

            <div class="relative flex justify-center items-center py-12 lg:py-0">
              <div
                class="absolute inset-0 border border-amber-500/10 rounded-full animate-orbit-slow"
              ></div>

              <div class="relative z-10">
                <div class="relative overflow-hidden rounded-3xl">
                  <img
                    src="@/assets/Man.png"
                    class="max-h-[65vh] lg:max-h-[75vh] object-contain drop-shadow-[0_0_50px_rgba(251,191,36,0.1)] transition-all duration-1000 ease-in-out breathing-image"
                    alt="Subrahmanyam Konakanchi"
                  />
                </div>

                <div
                  class="absolute -bottom-6 -right-6 lg:-right-12 bg-neutral-900 border border-neutral-800 p-5 rounded-2xl shadow-2xl backdrop-blur-xl"
                >
                  <p
                    class="text-[9px] font-mono text-amber-500 uppercase font-bold mb-2 tracking-widest"
                  >
                    Human_Location
                  </p>
                  <p class="text-sm font-bold text-white italic">Delray Beach, FL</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section
    id="about"
    class="snap-start min-h-screen w-full bg-neutral-950 relative overflow-hidden flex items-center justify-center bg-terminal-lines"
  >
    <div
      class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] bg-amber-500/5 rounded-full blur-[120px] pointer-events-none"
    ></div>

    <div class="max-w-7xl mx-auto px-6 lg:px-24 w-full reveal-on-scroll relative z-10">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-20 items-center">
        <div class="lg:col-span-7 space-y-8 lg:space-y-10">
          <div class="space-y-2">
            <h2 class="text-amber-500 font-mono tracking-[0.4em] uppercase text-[10px] font-bold">
              Nice to meet you
            </h2>
            <h1
              class="text-5xl lg:text-7xl font-black italic uppercase tracking-tighter leading-tight text-white"
            >
              I build systems with <span class="text-neutral-700">soul.</span>
            </h1>
          </div>

          <div class="space-y-6 text-lg text-gray-300 leading-relaxed font-light">
            <p>
              I’m <span class="text-white font-medium">Subrahmanyam</span>—a curious builder and a
              Computer Engineering graduate from the University of Florida. To me, code isn't just
              lines of logic; it’s a tool for crafting
              <span class="text-amber-400/80 italic">meaningful experiences</span>.
            </p>

            <p>
              Whether I'm architecting a complex backend or refining a user interface, I focus on
              the "why" behind the "how." I’ve spent over six years bridging the gap between
              <span class="text-white font-medium italic">robust engineering</span> and
              <span class="text-white font-medium">human impact</span>, ensuring that every
              deployment is as maintainable as it is powerful.
            </p>

            <p>
              Beyond the screen, you’ll find me playing the
              <span class="text-amber-500 font-medium italic">flute</span>, hiking local trails, or
              geeking out over a new framework. I believe the best software comes from a blend of
              technical rigor and a creative spirit.
            </p>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-3 gap-6 pt-4">
            <div class="flex flex-col gap-2">
              <span class="text-amber-500 font-mono text-[10px] uppercase font-bold tracking-widest"
                >The Teacher</span
              >
              <p class="text-xs text-neutral-500">
                I get immense joy from teaching—from recursion to Docker.
              </p>
            </div>
            <div class="flex flex-col gap-2 border-l border-neutral-800 pl-6">
              <span class="text-amber-500 font-mono text-[10px] uppercase font-bold tracking-widest"
                >The Tinkerer</span
              >
              <p class="text-xs text-neutral-500">
                Always happy to automate away daily annoyances with code.
              </p>
            </div>
            <div class="flex flex-col gap-2 border-l border-neutral-800 pl-6">
              <span class="text-amber-500 font-mono text-[10px] uppercase font-bold tracking-widest"
                >The Listener</span
              >
              <p class="text-xs text-neutral-500">
                Always hunting for new music or a cool idea to collaborate on.
              </p>
            </div>
          </div>
        </div>

        <div class="lg:col-span-5 flex justify-center items-center">
          <div class="relative group">
            <div
              class="absolute -inset-4 border border-neutral-800 rounded-full animate-[spin_30s_linear_infinite] pointer-events-none"
            ></div>

            <div class="relative z-10 overflow-hidden rounded-2xl bg-neutral-900 shadow-2xl">
              <img
                src="@/assets/megreet.png"
                alt="Subrahmanyam Konakanchi"
                class="max-h-[500px] xl:max-h-[550px] w-auto object-contain transition-transform duration-700 group-hover:scale-105"
              />

              <div
                class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col justify-end p-8"
              >
                <p class="text-amber-500 font-mono text-[10px] uppercase mb-1">Status</p>
                <p class="text-sm font-bold italic uppercase text-white">
                  Lifelong Learner. Curious Builder.
                </p>
              </div>
            </div>

            <div
              class="absolute -bottom-6 -left-6 lg:bottom-10 lg:-left-20 bg-amber-500 p-6 rounded-lg rotate-[-3deg] shadow-xl hidden md:block"
            >
              <p class="text-black font-black text-xl leading-none italic uppercase">
                FLORIDA<br />BASED
              </p>
              <p
                class="text-black/60 font-mono text-[10px] mt-1 font-bold uppercase tracking-tighter"
              >
                U_Florida :: MS
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section
    id="education"
    class="snap-start min-h-screen w-full bg-black flex items-center justify-center border-t border-neutral-900 bg-dot-matrix relative overflow-hidden"
  >
    <div class="max-w-7xl mx-auto px-6 lg:px-24 w-full reveal-on-scroll py-20">
      <div class="flex flex-col lg:flex-row items-stretch justify-center gap-10 lg:gap-20">
        <div class="lg:w-[30%] flex items-center justify-center">
          <div class="lg:sticky lg:top-1/2 lg:-translate-y-1/2 text-center">
            <h1
              class="text-6xl lg:text-7xl font-black italic tracking-tighter text-transparent bg-clip-text bg-gradient-to-br from-white via-gray-300 to-neutral-700 leading-[0.9]"
            >
              EDU<br /><span class="text-amber-400/90">CATION</span>
            </h1>
            <div class="w-12 h-1 bg-amber-400 mx-auto mt-6 rounded-full"></div>
          </div>
        </div>

        <div class="hidden lg:flex w-[4px] relative justify-center">
          <div
            class="absolute inset-0 bg-gradient-to-b from-amber-400 via-neutral-800 to-transparent w-full rounded-full"
          ></div>
        </div>

        <div class="w-full lg:w-[65%] flex flex-col gap-16 lg:gap-24 justify-center">
          <div
            v-for="(edu, index) in educationHistory"
            :key="index"
            class="flex justify-start items-start"
          >
            <div
              class="flex flex-col md:flex-row items-stretch transition-all duration-1000 ease-out w-full shadow-2xl"
            >
              <div
                class="w-full md:w-[320px] border-2 border-amber-400 bg-black z-20 overflow-hidden transition-all duration-700"
                :class="
                  eduExpanded[index]
                    ? 'rounded-t-lg md:rounded-t-none md:rounded-l-lg'
                    : 'rounded-lg'
                "
              >
                <div class="h-32 border-b-2 border-amber-400 overflow-hidden">
                  <img :src="edu.image" class="w-full h-full object-cover opacity-60" />
                </div>
                <div class="p-6 bg-black">
                  <h2 class="text-xl font-bold text-center tracking-tight text-white uppercase">
                    {{ edu.university }}
                  </h2>
                  <div class="mt-4 text-center text-gray-400 border-t border-gray-800 pt-4">
                    <p class="text-xs font-medium">{{ edu.location }}</p>
                    <p class="text-xs font-mono tracking-widest text-amber-200/70 mt-1">
                      {{ edu.period }}
                    </p>
                  </div>
                </div>
              </div>

              <div
                class="transition-all duration-1000 ease-in-out border-amber-400 bg-neutral-900/40 backdrop-blur-md overflow-hidden"
                :class="
                  eduExpanded[index]
                    ? 'p-8 border-2 border-t-0 md:border-t-2 md:border-l-0 rounded-b-lg md:rounded-b-none md:rounded-r-lg w-full md:w-[480px] opacity-100 h-auto'
                    : 'w-0 opacity-0 h-0 p-0 border-0'
                "
              >
                <div class="min-w-full md:min-w-[400px]">
                  <h4
                    class="text-amber-400 uppercase text-[10px] font-mono font-bold tracking-[0.3em] mb-6"
                  >
                    Academic Achievement
                  </h4>
                  <div class="space-y-4">
                    <p class="text-lg font-semibold leading-tight text-white">
                      {{ edu.degree }}
                    </p>
                    <div class="pt-4 border-t border-gray-800">
                      <span class="text-gray-400 text-xs italic">Academic Standing:</span>
                      <p class="text-3xl font-black text-amber-400 mt-1">CGPA: {{ edu.cgpa }}</p>
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
  <div class="relative w-full bg-white overflow-hidden" style="height: 120px">
    <svg class="absolute bottom-0 w-full h-full" viewBox="0 0 100 100" preserveAspectRatio="none">
      <polygon fill="black" points="0,100 100,100 100,0 0,100" />

      <line x1="0" y1="100" x2="100" y2="0" stroke="#fbbf24" stroke-width="1" />
    </svg>
  </div>

  <section id="experience" class="min-h-screen bg-neutral-950 py-32 border-y border-neutral-900">
    <div class="max-w-7xl mx-auto px-6 lg:px-24">
      <div class="min-h-screen bg-black text-white p-4 md:p-10 relative overflow-x-hidden">
        <div class="flex flex-col lg:flex-row w-full max-w-[1440px] mx-auto min-h-screen">
          <div class="w-full lg:w-[65%] flex flex-col gap-32 py-20 lg:pr-16">
            <div
              v-for="(job, index) in workHistory"
              :key="index"
              class="flex justify-end items-start"
            >
              <div
                class="flex flex-col md:flex-row items-stretch transition-all duration-1000 ease-out w-full"
                :class="workExpanded[index] ? 'md:max-w-[840px]' : 'md:max-w-[320px]'"
              >
                <div
                  @click="toggleWork(index)"
                  class="w-full md:w-[320px] flex-shrink-0 border-2 border-amber-400 p-8 bg-black z-20 shadow-[0_0_15px_rgba(251,191,36,0.1)] transition-all duration-700 cursor-pointer hover:bg-neutral-900"
                  :class="
                    workExpanded[index]
                      ? 'rounded-t-lg md:rounded-t-none md:rounded-l-lg'
                      : 'rounded-lg'
                  "
                >
                  <h2 class="text-2xl font-bold text-center tracking-tight text-white">
                    {{ job.company }}
                  </h2>
                  <h3 class="text-lg text-center text-amber-300 mt-2 font-medium">
                    {{ job.role }}
                  </h3>
                  <div
                    class="mt-8 space-y-2 text-center text-gray-400 border-t border-gray-800 pt-6"
                  >
                    <p class="text-sm font-medium">{{ job.location }}</p>
                    <p class="text-xs font-mono tracking-widest text-amber-200/70">
                      {{ job.period }}
                    </p>
                  </div>
                </div>

                <div
                  class="grid transition-all duration-700 ease-in-out overflow-hidden border-amber-400 bg-neutral-900/50 backdrop-blur-sm"
                  :class="[
                    workExpanded[index]
                      ? 'grid-rows-[1fr] opacity-100 border-2 border-t-0 md:border-t-2 md:border-l-0 rounded-b-lg md:rounded-b-none md:rounded-r-lg'
                      : 'grid-rows-[0fr] opacity-0 border-0 md:w-0',
                  ]"
                >
                  <div class="overflow-hidden">
                    <div class="p-8 w-full md:w-[520px]">
                      <h4 class="text-amber-400 uppercase text-xs font-bold tracking-[0.2em] mb-6">
                        Key Contributions
                      </h4>
                      <ul class="space-y-5 text-sm leading-relaxed text-gray-100">
                        <li v-for="bullet in job.bullets" :key="bullet" class="flex gap-4">
                          <span class="text-amber-400 text-lg leading-none">•</span>
                          <span v-html="bullet"></span>
                        </li>
                      </ul>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="hidden lg:flex w-[4px] relative justify-center">
            <div
              class="absolute inset-0 bg-gradient-to-b from-amber-400 via-neutral-800 to-transparent w-full rounded-full"
            ></div>
          </div>

          <div class="hidden lg:flex flex-1 items-center justify-center lg:pl-16">
            <div class="sticky top-1/2 -translate-y-1/2 text-center">
              <h1
                class="text-7xl font-black italic tracking-tighter text-transparent bg-clip-text bg-gradient-to-br from-white via-gray-300 to-neutral-700 leading-[0.9]"
              >
                WORK<br /><span class="text-amber-400/90">HISTORY</span>
              </h1>
              <div class="w-12 h-1 bg-amber-400 mx-auto mt-6 rounded-full"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section id="projects" class="min-h-screen bg-black border-b border-neutral-900 overflow-hidden">
    <div class="w-full flex flex-col items-center reveal-on-scroll">
      <div class="bg-black text-white font-sans selection:bg-amber-500/30 w-full">
        <div class="py-20 text-center border-b border-neutral-900 w-full bg-neutral-950/50">
          <h2 class="text-xs uppercase tracking-[0.6em] text-amber-500 mb-4 font-bold">
            Portfolio
          </h2>
          <h1 class="text-4xl md:text-7xl font-black tracking-tighter italic">FEATURED PROJECTS</h1>
          <div class="w-20 h-1 bg-amber-400 mx-auto mt-6"></div>
        </div>

        <section
          class="flex flex-col lg:flex-row min-h-fit lg:min-h-[70vh] border-b border-neutral-900 justify-center"
        >
          <div
            class="w-full lg:w-1/2 bg-neutral-950 flex items-center justify-center p-8 lg:p-20 border-b lg:border-b-0 lg:border-r border-neutral-800"
          >
            <div
              class="relative z-10 w-full max-w-md aspect-video bg-black rounded-xl border border-amber-500/20 shadow-[0_0_50px_rgba(251,191,36,0.05)] flex flex-col items-center justify-center p-6 text-center"
            >
              <div class="w-12 h-0.5 bg-amber-500 mb-4"></div>
              <p class="text-amber-500 font-mono text-xs tracking-widest mb-2 uppercase">
                AWS Architecture
              </p>
              <p class="text-gray-500 text-[10px]">Lambda • S3 • DynamoDB • PostgreSQL</p>
            </div>
          </div>
          <div
            class="w-full lg:w-1/2 p-8 md:p-16 lg:p-20 flex flex-col justify-center items-center lg:items-start bg-black"
          >
            <div class="max-w-md w-full">
              <span
                class="px-2 py-0.5 bg-amber-500/10 text-amber-500 text-[10px] font-bold rounded tracking-widest uppercase block w-fit mb-4"
                >Full Stack</span
              >
              <h2
                class="text-4xl md:text-5xl font-bold tracking-tight text-center lg:text-left mb-6"
              >
                LegalBill Pro
              </h2>
              <p
                class="text-base md:text-lg text-gray-400 mb-8 leading-relaxed font-light text-center lg:text-left"
              >
                Designed a full-stack billing platform for a Washington law firm. Automated the
                payment lifecycle for 12,000+ annual invoices, reducing collection time
                significantly.
              </p>
              <div class="grid grid-cols-2 gap-6 mb-10">
                <div class="border-l-2 border-amber-500 pl-4 text-center lg:text-left">
                  <p class="text-2xl md:text-3xl font-black text-white">69%</p>
                  <p class="text-[10px] text-gray-500 uppercase tracking-widest mt-1">
                    Efficiency Boost
                  </p>
                </div>
                <div class="border-l-2 border-amber-500 pl-4 text-center lg:text-left">
                  <p class="text-2xl md:text-3xl font-black text-white">14 Days</p>
                  <p class="text-[10px] text-gray-500 uppercase tracking-widest mt-1">
                    Avg. Collection
                  </p>
                </div>
              </div>
              <div
                class="flex flex-wrap justify-center lg:justify-start gap-3 text-[10px] font-mono text-amber-500/60 uppercase"
              >
                <span>React</span> <span>•</span> <span>AWS Serverless</span> <span>•</span>
                <span>Django</span>
              </div>
            </div>
          </div>
        </section>

        <section
          class="flex flex-col lg:flex-row-reverse min-h-fit lg:min-h-[70vh] border-b border-neutral-900 justify-center"
        >
          <div
            class="w-full lg:w-1/2 bg-neutral-950 flex items-center justify-center p-8 lg:p-20 border-b lg:border-b-0 lg:border-l border-neutral-800"
          >
            <div
              class="w-64 h-64 md:w-80 md:h-80 aspect-square rounded-full border border-amber-500/10 flex flex-col items-center justify-center text-center p-8 relative"
            >
              <div
                class="absolute inset-0 rounded-full border border-amber-500/5 animate-ping"
              ></div>
              <h3 class="text-amber-500 font-mono tracking-tighter text-xl mb-4">NLP ENGINE</h3>
              <p class="text-gray-500 text-xs font-mono italic">Transformer-Based Translation</p>
            </div>
          </div>
          <div
            class="w-full lg:w-1/2 p-8 md:p-16 lg:p-20 flex flex-col justify-center items-center lg:items-end bg-black"
          >
            <div class="max-w-md w-full">
              <span
                class="px-2 py-0.5 bg-amber-500/10 text-amber-500 text-[10px] font-bold rounded tracking-widest uppercase block w-fit mb-4 lg:ml-auto"
                >AI & NLP</span
              >
              <h2
                class="text-4xl md:text-5xl font-bold tracking-tight text-center lg:text-right mb-6"
              >
                Quantify
              </h2>
              <p
                class="text-base md:text-lg text-gray-400 mb-8 leading-relaxed font-light text-center lg:text-right"
              >
                AI translation platform utilizing Helsinki-NLP Transformer models. Engineered an
                analysis suite leveraging Whisper for speech recognition and spaCy for document
                classification.
              </p>
              <ul class="space-y-3 mb-10 text-center lg:text-right">
                <li
                  class="text-gray-300 text-sm flex items-center justify-center lg:justify-end gap-3"
                >
                  High-accuracy transcription
                  <div class="hidden lg:block w-1.5 h-1.5 bg-amber-500 rounded-full"></div>
                </li>
                <li
                  class="text-gray-300 text-sm flex items-center justify-center lg:justify-end gap-3"
                >
                  Helsinki-NLP Models
                  <div class="hidden lg:block w-1.5 h-1.5 bg-amber-500 rounded-full"></div>
                </li>
              </ul>
              <div
                class="flex flex-wrap justify-center lg:justify-end gap-3 text-[10px] font-mono text-amber-500/60 uppercase"
              >
                <span>Django</span> <span>•</span> <span>React</span> <span>•</span>
                <span>Transformers</span>
              </div>
            </div>
          </div>
        </section>

        <section
          class="flex flex-col lg:flex-row min-h-fit lg:min-h-[70vh] border-b border-neutral-900 justify-center"
        >
          <div
            class="w-full lg:w-1/2 bg-neutral-950 flex items-center justify-center p-8 lg:p-20 border-b lg:border-b-0 lg:border-r border-neutral-800"
          >
            <div
              class="w-full max-w-md p-8 bg-black rounded-lg border border-neutral-800 shadow-2xl"
            >
              <div class="flex items-end gap-2 h-32 md:h-40">
                <div class="flex-1 bg-amber-500/10 h-1/4 animate-pulse"></div>
                <div class="flex-1 bg-amber-500/30 h-1/2 animate-pulse delay-75"></div>
                <div class="flex-1 bg-amber-500/60 h-3/4 animate-pulse delay-150"></div>
                <div class="flex-1 bg-amber-500/20 h-1/3 animate-pulse delay-100"></div>
                <div class="flex-1 bg-amber-500/90 h-full animate-pulse delay-200"></div>
              </div>
            </div>
          </div>
          <div
            class="w-full lg:w-1/2 p-8 md:p-16 lg:p-20 flex flex-col justify-center items-center lg:items-start bg-black"
          >
            <div class="max-w-md w-full">
              <span
                class="px-2 py-0.5 bg-amber-500/10 text-amber-500 text-[10px] font-bold rounded tracking-widest uppercase block w-fit mb-4"
                >Big Data</span
              >
              <h2
                class="text-4xl md:text-5xl font-bold tracking-tight text-center lg:text-left mb-6"
              >
                TrendNavigator
              </h2>
              <p
                class="text-base md:text-lg text-gray-400 mb-8 leading-relaxed font-light text-center lg:text-left"
              >
                Built an interactive dashboard to process 10M+ economic data points. Optimized
                client-side performance for dynamic trend analysis across 200+ countries.
              </p>
              <div class="grid grid-cols-2 gap-6 mb-10">
                <div class="border-l-2 border-amber-500 pl-4 text-center lg:text-left">
                  <p class="text-2xl md:text-3xl font-black text-white">10M+</p>
                  <p class="text-[10px] text-gray-500 uppercase tracking-widest mt-1">
                    Data Points
                  </p>
                </div>
                <div class="border-l-2 border-amber-500 pl-4 text-center lg:text-left">
                  <p class="text-2xl md:text-3xl font-black text-white">D3.js</p>
                  <p class="text-[10px] text-gray-500 uppercase tracking-widest mt-1">
                    Rendering Engine
                  </p>
                </div>
              </div>
              <div
                class="flex flex-wrap justify-center lg:justify-start gap-3 text-[10px] font-mono text-amber-500/60 uppercase"
              >
                <span>React</span> <span>•</span> <span>D3.js</span> <span>•</span>
                <span>PostgreSQL</span>
              </div>
            </div>
          </div>
        </section>
      </div>
    </div>
  </section>

  <!-- <div class="min-h-screen bg-black text-white p-10 lg:p-24 border-t border-neutral-900">
    <div class="mb-20">
      <h2 class="text-amber-500 font-mono tracking-[0.3em] uppercase text-sm mb-2">Recognition</h2>
      <h1 class="text-6xl font-black italic uppercase">Achievements</h1>
    </div>

    <div class="grid grid-cols-1 lg:grid-cols-12 gap-16">
      <div class="lg:col-span-7">
        <h3 class="text-2xl font-bold mb-10 flex items-center gap-4">
          <span class="text-amber-500">01.</span> Hackathon Wins
        </h3>

        <div class="space-y-6">
          <div
            v-for="(hack, i) in hackathons"
            :key="i"
            class="group relative border-2 border-neutral-800 bg-neutral-900/30 p-8 rounded-2xl hover:border-amber-500/50 transition-all duration-500"
          >
            <div class="flex justify-between items-start mb-4">
              <div>
                <h4 class="text-xl font-bold group-hover:text-amber-400 transition-colors">
                  {{ hack.title }}
                </h4>
                <p class="text-amber-500 font-mono text-[10px] mt-1 uppercase tracking-widest">
                  {{ hack.issuer }}
                </p>
                <p class="text-amber-200/60 font-medium text-xs mt-1">{{ hack.award }}</p>
              </div>
              <span class="text-neutral-600 font-mono text-sm">{{ hack.date }}</span>
            </div>
            <p class="text-gray-400 text-sm leading-relaxed" v-html="hack.description"></p>
          </div>
        </div>
      </div>

      <div class="lg:col-span-5 border-l border-neutral-800 lg:pl-16">
        <h3 class="text-2xl font-bold mb-10 flex items-center gap-4">
          <span class="text-amber-500">02.</span> Publications
        </h3>

        <div class="space-y-12">
          <div v-for="(pub, j) in publications" :key="j" class="relative">
            <div
              class="absolute -left-[69px] top-2 w-4 h-4 bg-amber-500 rounded-full border-4 border-black"
            ></div>
            <p class="text-xs font-mono text-neutral-500 mb-2 uppercase">{{ pub.journal }}</p>
            <h4 class="text-lg font-bold leading-snug mb-3">{{ pub.title }}</h4>
            <p class="text-sm text-gray-400 mb-4">{{ pub.abstract }}</p>
            <a
              :href="pub.link"
              class="text-amber-500 text-xs font-bold uppercase tracking-widest hover:underline"
              >View Paper →</a
            >
          </div>
        </div>
      </div>
    </div>
  </div> -->

  <section
    id="achievements"
    class="min-h-screen bg-black py-20 lg:py-32 border-b border-neutral-900"
  >
    <div class="max-w-[1440px] mx-auto px-6 lg:px-16">
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
          <h1 class="text-4xl md:text-7xl font-black italic uppercase tracking-tighter">
            Engineering <span class="text-neutral-800">Arsenal</span>
          </h1>
          <div class="w-16 h-1 bg-amber-500 mx-auto mt-6"></div>
        </div>

        <div class="relative flex flex-col items-center gap-8 lg:block w-full h-auto lg:h-[900px]">
          <div
            ref="hubRef"
            class="hidden lg:flex absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 z-30 w-52 h-52 rounded-full border-2 border-amber-500 bg-black flex-col items-center justify-center p-4 shadow-[0_0_100px_rgba(251,191,36,0.15)]"
          >
            <h3 class="text-xl font-black text-center leading-none">
              CORE<br /><span class="text-amber-500">GATEWAY</span>
            </h3>
            <p class="text-[8px] font-mono text-gray-500 mt-3 uppercase tracking-widest">
              Stack Architecture
            </p>
          </div>

          <div
            v-for="(node, index) in nodes"
            :key="index"
            :ref="(el) => (nodeRefs[index] = el)"
            :class="[
              'w-full max-w-sm lg:absolute lg:w-72 bg-neutral-900/40 backdrop-blur-xl border border-neutral-800 p-6 rounded-2xl hover:border-amber-500/60 transition-all duration-500 z-20 group',
              node.pos,
            ]"
          >
            <div class="flex items-center gap-3 mb-5 border-b border-neutral-800 pb-3">
              <div
                class="w-1.5 h-1.5 bg-amber-500 rounded-full animate-pulse group-hover:scale-150 transition-transform"
              ></div>
              <h4 class="text-[11px] font-mono font-black uppercase text-amber-500 tracking-widest">
                {{ node.title.replace('_', ' ') }}
              </h4>
            </div>
            <ul class="grid grid-cols-2 lg:grid-cols-1 gap-y-2 lg:gap-y-3">
              <li
                v-for="skill in node.skills"
                :key="skill"
                class="flex items-center justify-between text-[11px] lg:text-xs text-neutral-400 group-hover:text-neutral-200 transition-colors"
              >
                <span>{{ skill }}</span>
                <div
                  class="hidden lg:block w-1 h-1 bg-neutral-800 rounded-full group-hover:bg-amber-500/50"
                ></div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section id="contact" class="min-h-screen bg-neutral-950 py-20 lg:py-32">
    <div class="max-w-[1440px] mx-auto px-6 lg:px-16 reveal-on-scroll">
      <div
        class="min-h-screen bg-black text-white p-6 md:p-12 lg:p-24 border-t border-neutral-900 relative overflow-hidden flex flex-col justify-center rounded-3xl"
        ref="containerRef"
      >
        <div
          class="absolute top-0 right-0 w-64 h-64 lg:w-96 lg:h-96 bg-amber-500/5 rounded-full blur-[80px] lg:blur-[120px] pointer-events-none"
        ></div>

        <div class="w-full grid grid-cols-1 lg:grid-cols-2 gap-16 lg:gap-24 items-center">
          <div
            class="relative z-10 flex flex-col items-center lg:items-start text-center lg:text-left"
          >
            <h2 class="text-amber-500 font-mono tracking-[0.5em] uppercase text-xs mb-4 font-bold">
              Connection Port
            </h2>
            <h1
              class="text-5xl md:text-7xl font-black italic uppercase tracking-tighter mb-8 leading-none"
            >
              Get In <span class="text-neutral-800">Touch</span>
            </h1>

            <p class="text-gray-400 text-base md:text-lg leading-relaxed mb-10 max-w-md">
              Currently based in <span class="text-white font-bold">Florida, USA</span>. I am open
              to discussing new ventures, system architecture consulting, or high-scale engineering
              opportunities.
            </p>

            <div class="w-full max-w-md space-y-4">
              <a
                href="mailto:lc.subrahmanyam@gmail.com"
                class="group flex items-center gap-4 p-4 border border-neutral-800 rounded-xl hover:border-amber-500/50 transition-all bg-neutral-900/20"
              >
                <div
                  class="w-12 h-12 flex-shrink-0 rounded-lg bg-neutral-800 flex items-center justify-center group-hover:bg-amber-500 transition-colors"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-5 w-5 text-amber-500 group-hover:text-black"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
                    />
                  </svg>
                </div>
                <div class="text-left">
                  <p class="text-[9px] font-mono text-neutral-600 uppercase tracking-widest">
                    Primary Channel
                  </p>
                  <p class="text-sm md:text-base font-bold">lc.subrahmanyam@gmail.com</p>
                </div>
              </a>

              <div class="grid grid-cols-3 gap-3">
                <a
                  v-for="link in socialLinks"
                  :key="link.name"
                  :href="link.url"
                  class="py-3 border border-neutral-800 rounded-xl hover:bg-neutral-900 text-center transition-all group"
                >
                  <span
                    class="text-[10px] font-mono text-neutral-500 group-hover:text-amber-500 uppercase tracking-widest"
                  >
                    {{ link.name }}
                  </span>
                </a>
              </div>
            </div>
          </div>

          <div
            class="w-full max-w-lg mx-auto lg:ml-auto bg-neutral-900/40 border border-neutral-800 p-6 md:p-10 rounded-2xl relative shadow-2xl"
          >
            <div
              class="absolute -top-3 left-6 px-3 bg-black border border-neutral-800 rounded text-[9px] font-mono text-amber-500 uppercase tracking-widest"
            >
              Incoming_Transmission
            </div>

            <form class="space-y-6 mt-4">
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="space-y-2">
                  <label class="block text-[10px] font-mono text-neutral-500 uppercase"
                    >Source_Name</label
                  >
                  <input
                    type="text"
                    class="w-full bg-black border border-neutral-800 rounded-lg p-3 text-sm focus:border-amber-500 outline-none transition-all placeholder:text-neutral-700"
                    placeholder="Your Name"
                  />
                </div>
                <div class="space-y-2">
                  <label class="block text-[10px] font-mono text-neutral-500 uppercase"
                    >Contact_Identity</label
                  >
                  <input
                    type="email"
                    class="w-full bg-black border border-neutral-800 rounded-lg p-3 text-sm focus:border-amber-500 outline-none transition-all placeholder:text-neutral-700"
                    placeholder="email@example.com"
                  />
                </div>
              </div>
              <div class="space-y-2">
                <label class="block text-[10px] font-mono text-neutral-500 uppercase"
                  >Payload_Message</label
                >
                <textarea
                  rows="4"
                  class="w-full bg-black border border-neutral-800 rounded-lg p-3 text-sm focus:border-amber-500 outline-none transition-all placeholder:text-neutral-700 resize-none"
                  placeholder="Briefly describe your project or inquiry..."
                ></textarea>
              </div>
              <button
                class="w-full py-4 bg-amber-500 text-black font-black uppercase tracking-widest rounded-lg hover:bg-amber-400 transition-all flex items-center justify-center gap-3 active:scale-95"
              >
                Execute Send
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                >
                  <path
                    d="M10.894 2.553a1 1 0 00-1.788 0l-7 14a1 1 0 001.169 1.409l5-1.429A1 1 0 009 15.571V11a1 1 0 112 0v4.571a1 1 0 00.725.962l5 1.428a1 1 0 001.17-1.408l-7-14z"
                  />
                </svg>
              </button>
            </form>
          </div>
        </div>

        <div
          class="mt-24 lg:mt-32 text-center font-mono text-[9px] text-neutral-700 tracking-[0.3em] uppercase opacity-50"
        >
          Connection_Established // System_Handshake_Complete // 2026_Deployment
        </div>
      </div>
    </div>
  </section>

  <footer class="bg-black text-white p-12 border-t border-neutral-900 font-mono">
    <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-10">
      <div class="space-y-2">
        <div class="flex items-center gap-2">
          <div class="w-2 h-2 rounded-full bg-green-500 animate-pulse"></div>
          <p class="text-amber-500 text-[10px] uppercase tracking-widest font-bold">
            Node_Status: Online
          </p>
        </div>
        <p class="text-sm">root@skonakanchi:~$ <span class="animate-pulse">_</span></p>
      </div>

      <div class="flex gap-10">
        <a
          href="#"
          class="group text-xs uppercase tracking-widest text-neutral-400 hover:text-amber-500 transition-colors"
        >
          [ LinkedIn ]
        </a>
        <a
          href="#"
          class="group text-xs uppercase tracking-widest text-neutral-400 hover:text-amber-500 transition-colors"
        >
          [ GitHub ]
        </a>
        <a
          href="#"
          class="group text-xs uppercase tracking-widest text-neutral-400 hover:text-amber-500 transition-colors"
        >
          [ Email ]
        </a>
      </div>

      <div class="text-right">
        <p class="text-[9px] text-neutral-600 uppercase tracking-tighter">
          Deployment_v2.0.26 // Built with Vue 3 & Tailwind // Florida, USA
        </p>
      </div>
    </div>
  </footer>
</template>
