<template>
  <section id="services" class="services-section">
    <div class="container">
      <div class="section-header fade-in">
        <span class="section-badge">What We Do</span>
        <h2>Services That Drive <span class="accent">Growth</span></h2>
        <p class="section-subtitle">
          End-to-end digital solutions tailored to your brand's needs.
        </p>
      </div>

      <div class="services-grid fade-in">
        <div
          v-for="service in services"
          :key="service.title"
          class="service-card"
        >
          <div class="service-icon">{{ service.icon }}</div>
          <h3>{{ service.title }}</h3>
          <p>{{ service.description }}</p>
          <a href="#contact" class="service-link">Learn More →</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const services = [
  {
    icon: '🎨',
    title: 'Brand Design',
    description: 'Visual identities that communicate your brand story with clarity and impact across every touchpoint.',
  },
  {
    icon: '💻',
    title: 'Web Development',
    description: 'Fast, accessible, and beautiful websites built with modern frameworks. From landing pages to complex apps.',
  },
  {
    icon: '📱',
    title: 'Social Media Marketing',
    description: 'Content strategy and management that grows engaged communities and drives real business results.',
  },
  {
    icon: '📢',
    title: 'Digital Advertising',
    description: 'ROI-focused paid campaigns across Google, Meta, and LinkedIn that convert clicks into customers.',
  },
  {
    icon: '📊',
    title: 'Analytics & SEO',
    description: 'Data-driven insights and search optimization that put your brand in front of the right audience.',
  },
  {
    icon: '🎬',
    title: 'Video Production',
    description: 'Compelling video content from concept to delivery — brand films, reels, explainers, and more.',
  },
]
</script>
