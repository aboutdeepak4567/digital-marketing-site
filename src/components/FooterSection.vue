<template>
  <footer>
    <div class="footer-container container">
      <div
        v-for="column in columns"
        :key="column.heading"
        class="link-column"
      >
        <h4>{{ column.heading }}</h4>
        <a v-for="link in column.links" :key="link.label" href="#">
          {{ link.label }}
        </a>
      </div>
    </div>
  </footer>
</template>

<script setup>
const columns = [
  {
    heading: 'About',
    links: [
      { label: 'Our Story' },
      { label: 'Team' },
      { label: 'Careers' },
    ],
  },
  {
    heading: 'Services',
    links: [
      { label: 'Web Design' },
      { label: 'Development' },
      { label: 'Marketing' },
    ],
  },
]
</script>
