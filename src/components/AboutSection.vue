<template>
  <section id="about" class="about-section">
    <div class="container">

      <!-- Story -->
      <div class="about-story fade-in">
        <div class="about-text">
          <span class="section-badge">Who We Are</span>
          <h2>We Turn Ideas Into <span class="accent">Digital Reality</span></h2>
          <p>
            Founded in 2014, Creative Agency has helped over 200 brands craft standout digital
            experiences. We blend strategy, design, and technology to deliver results that matter.
          </p>
          <p>
            Our team of passionate creatives and engineers work together to build products that
            are not just beautiful — but effective and scalable.
          </p>
          <a href="#contact" class="primary-button" style="margin-top: 24px; display: inline-block;">
            Work With Us
          </a>
        </div>
        <div class="about-image">
          <img src="/images/about_agency.png" alt="About Creative Agency" />
        </div>
      </div>

      <!-- Stats -->
      <div class="stats-grid fade-in">
        <div v-for="stat in stats" :key="stat.label" class="stat-card">
          <span class="stat-number">{{ stat.display }}{{ stat.suffix }}</span>
          <span class="stat-label">{{ stat.label }}</span>
        </div>
      </div>

      <!-- Team -->
      <div class="team-header fade-in">
        <span class="section-badge">The Team</span>
        <h2>Meet The People Behind The Magic</h2>
      </div>
      <div class="team-grid fade-in">
        <div v-for="member in team" :key="member.name" class="team-card">
          <div class="team-avatar" :style="{ background: member.color }">
            {{ member.initials }}
          </div>
          <h4>{{ member.name }}</h4>
          <p>{{ member.role }}</p>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted, nextTick } from 'vue'

const stats = ref([
  { label: 'Clients Served',       target: 200, display: 0, suffix: '+' },
  { label: 'Projects Delivered',   target: 350, display: 0, suffix: '+' },
  { label: 'Years of Experience',  target: 10,  display: 0, suffix: '' },
  { label: 'Team Members',         target: 24,  display: 0, suffix: '' },
])

const team = [
  { name: 'Alex Carter',   role: 'CEO & Creative Director', initials: 'AC', color: '#5a58e9' },
  { name: 'Priya Sharma',  role: 'Lead Designer',           initials: 'PS', color: '#e95889' },
  { name: 'Marcus Lee',    role: 'Head of Development',     initials: 'ML', color: '#58e9a0' },
  { name: 'Sofia Nguyen',  role: 'Marketing Strategist',    initials: 'SN', color: '#e9b058' },
]

function animateCounters() {
  stats.value.forEach((stat) => {
    const duration = 1800
    const step = stat.target / (duration / 16)
    const timer = setInterval(() => {
      stat.display = Math.min(Math.round(stat.display + step), stat.target)
      if (stat.display >= stat.target) clearInterval(timer)
    }, 16)
  })
}

let observer
onMounted(() => {
  nextTick(() => {
    observer = new IntersectionObserver(
      (entries) => {
        if (entries[0].isIntersecting) {
          animateCounters()
          observer.disconnect()
        }
      },
      { threshold: 0.3 }
    )
    const el = document.querySelector('.stats-grid')
    if (el) observer.observe(el)
  })
})
onUnmounted(() => { if (observer) observer.disconnect() })

</script>
