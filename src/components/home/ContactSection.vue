<script setup lang="ts">
import { ref } from 'vue'

const form = ref({ name: '', email: '', message: '' })
const submitted = ref(false)

const handleSubmit = () => {
  if (!form.value.name || !form.value.email || !form.value.message) return
  // In a real app, send to API
  submitted.value = true
}

const socialLinks = [
  {
    name: 'LinkedIn',
    handle: 'subrahmanyam-konakanchi',
    url: 'https://linkedin.com/in/subrahmanyam-konakanchi-91ba651bb/',
    icon: `<path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/>`,
  },
  {
    name: 'GitHub',
    handle: 'Subrahmanyam01',
    url: 'https://github.com/Subrahmanyam01',
    icon: `<path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 00-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0020 4.77 5.07 5.07 0 0019.91 1S18.73.65 16 2.48a13.38 13.38 0 00-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 005 4.77a5.44 5.44 0 00-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 009 18.13V22"/>`,
  },
  {
    name: 'Email',
    handle: 'lc.subrahmanyam@gmail.com',
    url: 'mailto:lc.subrahmanyam@gmail.com',
    icon: `<path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/>`,
  },
]
</script>

<template>
  <section
    id="contact"
    class="relative min-h-screen bg-black py-24 lg:py-32 overflow-hidden border-b border-neutral-900"
  >
    <!-- Background -->
    <div class="absolute inset-0 z-0 pointer-events-none">
      <div
        class="absolute inset-0 bg-[linear-gradient(to_right,#80808008_1px,transparent_1px),linear-gradient(to_bottom,#80808008_1px,transparent_1px)] bg-[size:40px_40px]"
      ></div>
      <div class="absolute bottom-0 right-0 w-[60vw] h-[60vw] bg-amber-500/5 rounded-full blur-[160px]"></div>
    </div>

    <div class="max-w-[1440px] mx-auto px-6 lg:px-16 relative z-10 reveal-on-scroll">

      <!-- Header -->
      <div class="mb-16 lg:mb-20">
        <h2 class="text-xs uppercase tracking-[0.6em] text-amber-500 mb-4 font-bold font-mono">Connection Port</h2>
        <div class="flex flex-col lg:flex-row lg:items-end lg:justify-between gap-6">
          <h1 class="text-5xl md:text-7xl xl:text-8xl font-black tracking-tighter italic text-white leading-none">
            GET IN <br /><span class="text-neutral-700">TOUCH</span>
          </h1>
          <p class="text-gray-400 text-base lg:text-lg leading-relaxed font-light max-w-md lg:text-right">
            Open to new roles, interesting systems to architect, or just a good conversation about engineering.
          </p>
        </div>
        <div class="w-24 h-0.5 bg-gradient-to-r from-amber-500 to-transparent mt-10"></div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-20 items-start">

        <!-- Left: Social Links + Info -->
        <div class="flex flex-col gap-8">
          <!-- Primary email -->
          <a
            href="mailto:lc.subrahmanyam@gmail.com"
            class="group flex items-center gap-5 p-6 border border-neutral-800 rounded-2xl bg-neutral-950/60 hover:border-amber-500/40 hover:shadow-[0_0_40px_rgba(251,191,36,0.06)] transition-all duration-400"
          >
            <div class="w-12 h-12 rounded-xl bg-amber-500/10 border border-amber-500/30 flex items-center justify-center flex-shrink-0 group-hover:bg-amber-500 transition-colors duration-300">
              <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-amber-500 group-hover:text-black transition-colors" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
              </svg>
            </div>
            <div>
              <p class="text-[9px] font-mono text-neutral-600 uppercase tracking-widest mb-1">Primary Channel</p>
              <p class="text-sm lg:text-base font-bold text-white group-hover:text-amber-300 transition-colors">lc.subrahmanyam@gmail.com</p>
            </div>
            <svg class="w-4 h-4 text-neutral-700 group-hover:text-amber-500 ml-auto transition-all group-hover:translate-x-1 duration-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"/>
            </svg>
          </a>

          <!-- Social Links -->
          <div class="flex flex-col gap-3">
            <a
              v-for="link in socialLinks"
              :key="link.name"
              :href="link.url"
              target="_blank"
              class="group flex items-center gap-4 p-5 border border-neutral-800 rounded-xl bg-neutral-950/40 hover:border-amber-500/30 hover:bg-neutral-950/80 transition-all duration-300"
            >
              <div class="w-9 h-9 rounded-lg border border-neutral-700 flex items-center justify-center flex-shrink-0 group-hover:border-amber-500/40 transition-colors">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4 text-neutral-500 group-hover:text-amber-400 transition-colors" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5" v-html="link.icon"></svg>
              </div>
              <div class="flex-grow">
                <p class="text-[9px] font-mono text-neutral-600 uppercase tracking-widest">{{ link.name }}</p>
                <p class="text-sm font-medium text-neutral-400 group-hover:text-white transition-colors truncate">{{ link.handle }}</p>
              </div>
              <svg class="w-3.5 h-3.5 text-neutral-700 group-hover:text-amber-500 transition-all group-hover:translate-x-0.5 duration-300 shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"/>
              </svg>
            </a>
          </div>

          <!-- Status badge -->
          <div class="flex items-center gap-3 px-5 py-3 border border-green-500/20 bg-green-500/5 rounded-xl">
            <div class="w-2 h-2 rounded-full bg-green-400 animate-pulse shadow-[0_0_8px_rgba(74,222,128,0.7)]"></div>
            <p class="text-[10px] font-mono text-green-400/80 uppercase tracking-widest">Available for new opportunities</p>
          </div>
        </div>

        <!-- Right: Contact Form -->
        <div class="relative">
          <!-- Terminal-style top label -->
          <div class="absolute -top-3 left-6 px-3 bg-black border border-neutral-800 rounded text-[9px] font-mono text-amber-500 uppercase tracking-widest z-10">
            Incoming_Transmission
          </div>

          <div
            v-if="!submitted"
            class="bg-neutral-950/60 border border-neutral-800 rounded-2xl p-8 lg:p-10 relative overflow-hidden"
          >
            <div class="absolute inset-0 bg-gradient-to-br from-amber-500/3 to-transparent pointer-events-none"></div>

            <form class="space-y-6 relative z-10" @submit.prevent="handleSubmit">
              <div class="grid grid-cols-1 sm:grid-cols-2 gap-5">
                <div class="space-y-2">
                  <label class="block text-[9px] font-mono text-neutral-600 uppercase tracking-widest">Source_Name</label>
                  <input
                    v-model="form.name"
                    type="text"
                    placeholder="Your Name"
                    class="w-full bg-black border border-neutral-800 rounded-xl px-4 py-3 text-sm text-white placeholder:text-neutral-700 focus:border-amber-500/60 focus:outline-none transition-colors duration-200"
                  />
                </div>
                <div class="space-y-2">
                  <label class="block text-[9px] font-mono text-neutral-600 uppercase tracking-widest">Contact_ID</label>
                  <input
                    v-model="form.email"
                    type="email"
                    placeholder="email@example.com"
                    class="w-full bg-black border border-neutral-800 rounded-xl px-4 py-3 text-sm text-white placeholder:text-neutral-700 focus:border-amber-500/60 focus:outline-none transition-colors duration-200"
                  />
                </div>
              </div>

              <div class="space-y-2">
                <label class="block text-[9px] font-mono text-neutral-600 uppercase tracking-widest">Payload_Message</label>
                <textarea
                  v-model="form.message"
                  rows="5"
                  placeholder="Tell me about your project or opportunity..."
                  class="w-full bg-black border border-neutral-800 rounded-xl px-4 py-3 text-sm text-white placeholder:text-neutral-700 focus:border-amber-500/60 focus:outline-none transition-colors duration-200 resize-none"
                ></textarea>
              </div>

              <button
                type="submit"
                class="group w-full py-4 bg-amber-500 text-black font-black uppercase tracking-widest rounded-xl hover:bg-amber-400 active:scale-[0.98] transition-all duration-200 flex items-center justify-center gap-3 relative overflow-hidden"
              >
                <span class="relative z-10">Execute Transmission</span>
                <svg class="w-4 h-4 relative z-10 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M14 5l7 7m0 0l-7 7m7-7H3"/>
                </svg>
                <div class="absolute inset-0 bg-white opacity-0 group-hover:opacity-10 transition-opacity"></div>
              </button>
            </form>
          </div>

          <!-- Success State -->
          <div
            v-else
            class="bg-neutral-950/60 border border-green-500/30 rounded-2xl p-10 lg:p-16 flex flex-col items-center justify-center text-center gap-6"
          >
            <div class="w-16 h-16 rounded-full border border-green-500/40 bg-green-500/10 flex items-center justify-center">
              <svg class="w-7 h-7 text-green-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
              </svg>
            </div>
            <div>
              <p class="text-[9px] font-mono text-green-400/70 uppercase tracking-widest mb-2">Transmission Received</p>
              <p class="text-2xl font-black italic text-white">Message Sent!</p>
              <p class="text-neutral-500 text-sm mt-2">I'll get back to you shortly.</p>
            </div>
          </div>
        </div>

      </div>

      <!-- Footer note -->
      <div class="mt-20 text-center font-mono text-[9px] text-neutral-700 tracking-[0.3em] uppercase">
        Connection_Established // System_Handshake_Complete // 2026_Deployment
      </div>
    </div>
  </section>
</template>
