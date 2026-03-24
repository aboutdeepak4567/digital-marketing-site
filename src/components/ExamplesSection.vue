<template>
  <section id="services" class="examples-section">
    <div class="container">
      <div class="examples-header">
        <h2>Our Projects</h2>
      </div>

      <div class="examples-area flex">
        <div
          v-for="project in projects"
          :key="project.title"
          class="examples-card"
          :style="{ backgroundImage: `url('${project.image}')` }"
        >
          <div class="card-text">{{ project.title }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  { title: 'Project 1', image: '/images/banner.png' },
  { title: 'Project 2', image: '/images/logo.png' },
  { title: 'Project 3', image: '/images/advertisement.png' },
  { title: 'Project 4', image: '/images/thumbnail.png' },
]
</script>
