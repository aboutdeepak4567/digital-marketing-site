<template>
  <header id="home" class="header-section">
    <div class="container hero-inner">
      <div class="header-left fade-in">
        <div class="hero-badge">✦ Award-Winning Digital Agency</div>
        <h1>We Build Brands <span class="accent">That Stand Out</span></h1>
        <p>Modern, minimalistic, and results-driven design for ambitious businesses.</p>
        <div class="hero-stats">
          <span>🏆 200+ Clients</span>
          <span>⭐ 5-Star Rated</span>
          <span>📅 10 Yrs Experience</span>
        </div>
        <div class="hero-actions">
          <a href="#contact" class="primary-button">Get Started</a>
          <a href="#services" class="secondary-button">Our Services</a>
        </div>
      </div>

      <div class="header-right fade-in">
        <div
          class="hero-img-wrapper"
          @mousemove="onMouseMove"
          @mouseleave="onMouseLeave"
          :style="imgStyle"
        >
          <img src="/images/hero_illustration.png" alt="Creative Agency Digital Marketing" />
          <!-- Floating badge chips -->
          <div class="hero-chip chip-1">🎨 Brand Design</div>
          <div class="hero-chip chip-2">📈 ROI Focused</div>
          <div class="hero-chip chip-3">💡 Creative First</div>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const imgStyle = ref({})

function onMouseMove(e) {
  const rect = e.currentTarget.getBoundingClientRect()
  const x = ((e.clientX - rect.left) / rect.width - 0.5) * 18
  const y = ((e.clientY - rect.top) / rect.height - 0.5) * -18
  imgStyle.value = {
    transform: `perspective(900px) rotateY(${x}deg) rotateX(${y}deg) scale(1.03)`,
    transition: 'transform 0.1s ease',
  }
}

function onMouseLeave() {
  imgStyle.value = {
    transform: 'perspective(900px) rotateY(0deg) rotateX(0deg) scale(1)',
    transition: 'transform 0.5s ease',
  }
}
</script>
