<script setup lang="ts">
const socialLinks = [
  { name: 'LinkedIn', url: 'https://linkedin.com/in/subrahmanyam-konakanchi-91ba651bb/' },
  { name: 'GitHub', url: 'https://github.com/Subrahmanyam01' },
  { name: 'Email', url: 'mailto:lc.subrahmanyam@gmail.com' },
]
</script>

<template>
  <section id="contact" class="min-h-screen bg-neutral-950 py-20 lg:py-32">
    <div class="max-w-[1440px] mx-auto px-6 lg:px-16 reveal-on-scroll">
      <div
        class="min-h-screen bg-black text-white p-6 md:p-12 lg:p-24 border-t border-neutral-900 relative overflow-hidden flex flex-col justify-center rounded-3xl"
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
</template>
