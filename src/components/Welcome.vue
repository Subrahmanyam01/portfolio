<script setup lang="ts">
import { onMounted, onBeforeUnmount } from 'vue'
import HeroSection from './home/HeroSection.vue'
import AboutSection from './home/AboutSection.vue'
import EducationSection from './home/EducationSection.vue'
import ExperienceSection from './home/ExperienceSection.vue'
import ProjectsSection from './home/ProjectsSection.vue'
import AchievementsSection from './home/AchievementsSection.vue'
import SkillsSection from './home/SkillsSection.vue'
import ContactSection from './home/ContactSection.vue'
import TheFooter from './home/TheFooter.vue'

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

onMounted(() => {
  initScrollObserver()
})
</script>

<template>
  <main class="bg-black text-white selection:bg-amber-500/30 selection:text-amber-500 font-sans">
    <HeroSection />
    <AboutSection />
    <EducationSection />
    <ExperienceSection />
    <ProjectsSection />
    <AchievementsSection />
    <SkillsSection />
    <ContactSection />
    <TheFooter />
  </main>
</template>

<style>
/* Global Animations */
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
