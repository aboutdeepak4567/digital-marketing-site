<template>
  <nav class="main-nav" :class="{ 'scroll-header': isScrolled }">
    <div class="container nav-inner">
      <div class="company-logo">
        <img src="/images/logo.png" alt="Company Logo" />
        <span>Creative Agency</span>
      </div>

      <button class="nav-toggle" @click="toggleMenu" aria-label="Toggle navigation">
        <span></span><span></span><span></span>
      </button>

      <div class="nav-links" :class="{ active: isMenuOpen }">
        <ul>
          <li v-for="link in navLinks" :key="link.href">
            <a
              :href="link.href"
              :class="{ 'nav-active': activeSection === link.id }"
              @click="closeMenu"
            >{{ link.label }}</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useScrollSpy } from '../composables/useScrollSpy.js'

const navLinks = [
  { href: '#home',     id: 'home',     label: 'Home'    },
  { href: '#about',    id: 'about',    label: 'About'   },
  { href: '#services', id: 'services', label: 'Services'},
  { href: '#contact',  id: 'contact',  label: 'Contact' },
]

const { activeSection } = useScrollSpy(['home', 'about', 'services', 'contact'])

const isMenuOpen = ref(false)
const isScrolled  = ref(false)

function toggleMenu() { isMenuOpen.value = !isMenuOpen.value }
function closeMenu()  { isMenuOpen.value = false }

function handleScroll() { isScrolled.value = window.scrollY >= 80 }

onMounted(()  => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>
