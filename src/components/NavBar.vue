<template>
  <nav class="main-nav container flex" :class="{ 'scroll-header': isScrolled }">
    <div class="company-logo">
      <img src="/images/logo.png" alt="Company Logo" />
      <span>Creative Agency</span>
    </div>

    <button class="nav-toggle" @click="toggleMenu" aria-label="Toggle navigation">
      &#9776;
    </button>

    <div class="nav-links" :class="{ active: isMenuOpen }">
      <ul class="flex">
        <li><a href="#home" @click="closeMenu">Home</a></li>
        <li><a href="#about" @click="closeMenu">About</a></li>
        <li><a href="#services" @click="closeMenu">Services</a></li>
        <li><a href="#contact" @click="closeMenu">Contact</a></li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isMenuOpen = ref(false)
const isScrolled = ref(false)

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value
}

function closeMenu() {
  isMenuOpen.value = false
}

function handleScroll() {
  isScrolled.value = window.scrollY >= 200
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>
