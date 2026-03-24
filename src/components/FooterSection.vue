<template>
  <footer>
    <div class="container footer-inner">
      <div class="footer-brand">
        <img src="/images/logo.png" alt="Logo" width="40" />
        <span>Creative Agency</span>
        <p>Building digital experiences that inspire and convert.</p>
        <div class="footer-socials">
          <a href="#" aria-label="LinkedIn"  class="fsocial">in</a>
          <a href="#" aria-label="Twitter"   class="fsocial">𝕏</a>
          <a href="#" aria-label="Instagram" class="fsocial">ig</a>
          <a href="#" aria-label="GitHub"    class="fsocial">gh</a>
        </div>
      </div>

      <div v-for="col in columns" :key="col.heading" class="link-column">
        <h4>{{ col.heading }}</h4>
        <a v-for="link in col.links" :key="link" href="#">{{ link }}</a>
      </div>
    </div>

    <div class="footer-bottom">
      <p>© {{ year }} Creative Agency. All rights reserved.</p>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()

const columns = [
  {
    heading: 'Company',
    links: ['About Us', 'Our Team', 'Careers', 'Blog'],
  },
  {
    heading: 'Services',
    links: ['Brand Design', 'Web Development', 'Marketing', 'Analytics'],
  },
  {
    heading: 'Legal',
    links: ['Privacy Policy', 'Terms of Service', 'Cookie Policy'],
  },
]
</script>
