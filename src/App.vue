<template>
  <div>
    <NavBar />
    <HeroSection />
    <AboutSection />
    <ServicesSection />
    <ExamplesSection />
    <TestimonialsSection />
    <CtaSection />
    <ContactSection />
    <FooterSection />

    <!-- Scroll to top -->
    <button
      class="scroll-top-btn"
      :class="{ visible: showScrollTop }"
      @click="scrollToTop"
      aria-label="Scroll to top"
    >↑</button>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import NavBar            from './components/NavBar.vue'
import HeroSection       from './components/HeroSection.vue'
import AboutSection      from './components/AboutSection.vue'
import ServicesSection   from './components/ServicesSection.vue'
import ExamplesSection   from './components/ExamplesSection.vue'
import TestimonialsSection from './components/TestimonialsSection.vue'
import CtaSection        from './components/CtaSection.vue'
import ContactSection    from './components/ContactSection.vue'
import FooterSection     from './components/FooterSection.vue'

const showScrollTop = ref(false)

function handleScroll() {
  showScrollTop.value = window.scrollY >= 560
}
function scrollToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)

  // Fade-in on scroll
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((e) => {
        if (e.isIntersecting) {
          e.target.classList.add('visible')
          observer.unobserve(e.target)
        }
      })
    },
    { threshold: 0.12 }
  )
  document.querySelectorAll('.fade-in').forEach((el) => observer.observe(el))
})
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>
