<template>
  <section id="projects" class="examples-section">
    <div class="container">
      <div class="examples-header fade-in">
        <span class="section-badge">Portfolio</span>
        <h2>Our <span class="accent">Featured Projects</span></h2>
        <p class="section-subtitle">Click any project to explore it up close.</p>
      </div>

      <div class="examples-area fade-in">
        <div
          v-for="project in projects"
          :key="project.title"
          class="examples-card"
          :style="{ backgroundImage: `url('${project.image}')` }"
          @click="openLightbox(project)"
          @mousemove="onTilt($event, project)"
          @mouseleave="resetTilt(project)"
          :style-object="project.tiltStyle"
        >
          <div class="card-overlay"></div>
          <div class="card-content">
            <div class="card-tag">{{ project.tag }}</div>
            <div class="card-text">{{ project.title }}</div>
            <div class="card-cta">View Project →</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Lightbox Modal -->
    <teleport to="body">
      <transition name="lightbox-fade">
        <div v-if="lightboxProject" class="lightbox-overlay" @click.self="closeLightbox">
          <div class="lightbox-box">
            <button class="lightbox-close" @click="closeLightbox">✕</button>
            <img :src="lightboxProject.image" :alt="lightboxProject.title" />
            <div class="lightbox-info">
              <span class="section-badge">{{ lightboxProject.tag }}</span>
              <h3>{{ lightboxProject.title }}</h3>
              <p>{{ lightboxProject.description }}</p>
              <a href="#contact" class="primary-button" @click="closeLightbox">Start a Similar Project</a>
            </div>
          </div>
        </div>
      </transition>
    </teleport>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'

const projects = reactive([
  {
    title: 'Social Media Campaign',
    tag: 'Marketing',
    image: '/images/project_social_media.png',
    description: 'A viral social media campaign that drove 3M+ impressions and 40% engagement growth for a consumer lifestyle brand.',
    tiltStyle: {},
  },
  {
    title: 'Web Design & UI',
    tag: 'Design',
    image: '/images/project_web_design.png',
    description: 'A complete UX overhaul for a SaaS platform — from wireframes to polished, accessible interfaces that increased retention by 28%.',
    tiltStyle: {},
  },
  {
    title: 'Brand Identity',
    tag: 'Branding',
    image: '/images/project_branding.png',
    description: 'Full brand identity system including logo, typography, color palette, and stationery for a premium consulting firm.',
    tiltStyle: {},
  },
  {
    title: 'Ad Campaign ROI',
    tag: 'Advertising',
    image: '/images/project_advertising.png',
    description: 'A paid media strategy across Google and Meta that delivered 5× ROI and reduced cost-per-acquisition by 38%.',
    tiltStyle: {},
  },
])

const lightboxProject = ref(null)

function openLightbox(project) {
  lightboxProject.value = project
  document.body.style.overflow = 'hidden'
}
function closeLightbox() {
  lightboxProject.value = null
  document.body.style.overflow = ''
}

function onTilt(e, project) {
  const rect = e.currentTarget.getBoundingClientRect()
  const x = ((e.clientX - rect.left) / rect.width - 0.5) * 14
  const y = ((e.clientY - rect.top) / rect.height - 0.5) * -14
  project.tiltStyle = {
    transform: `perspective(700px) rotateY(${x}deg) rotateX(${y}deg) scale(1.04)`,
    transition: 'transform 0.08s ease',
    zIndex: 2,
  }
}
function resetTilt(project) {
  project.tiltStyle = {
    transform: 'perspective(700px) rotateY(0deg) rotateX(0deg) scale(1)',
    transition: 'transform 0.45s ease',
    zIndex: 1,
  }
}
</script>
