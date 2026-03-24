<template>
  <section class="testimonials-section">
    <div class="container">
      <div class="section-header fade-in">
        <span class="section-badge">Testimonials</span>
        <h2>What Our Clients <span class="accent">Say</span></h2>
      </div>

      <div class="testimonials-carousel fade-in">
        <button class="carousel-btn prev" @click="prev" aria-label="Previous">&#8249;</button>

        <transition name="slide" mode="out-in">
          <div :key="current" class="testimonial-card">
            <p class="quote">"{{ testimonials[current].quote }}"</p>
            <div class="testimonial-author">
              <div class="author-avatar" :style="{ background: testimonials[current].color }">
                {{ testimonials[current].initials }}
              </div>
              <div>
                <strong>{{ testimonials[current].name }}</strong>
                <span>{{ testimonials[current].company }}</span>
              </div>
            </div>
            <div class="stars">★★★★★</div>
          </div>
        </transition>

        <button class="carousel-btn next" @click="next" aria-label="Next">&#8250;</button>
      </div>

      <!-- Dots -->
      <div class="carousel-dots">
        <button
          v-for="(_, i) in testimonials"
          :key="i"
          class="dot"
          :class="{ active: i === current }"
          @click="current = i"
          :aria-label="`Go to testimonial ${i + 1}`"
        ></button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const testimonials = [
  {
    quote: "Creative Agency transformed our brand completely. The team's attention to detail and creative vision exceeded our expectations. Highly recommended!",
    name: 'Sarah Johnson',
    company: 'CEO, Bloom Retail',
    initials: 'SJ',
    color: '#5a58e9',
  },
  {
    quote: "From strategy to execution, they nailed every aspect of our digital campaign. Our conversion rate jumped 40% in the first month!",
    name: 'David Kim',
    company: 'CMO, NovaTech',
    initials: 'DK',
    color: '#e95889',
  },
  {
    quote: "Working with this team felt like having an in-house creative department. They're fast, professional, and genuinely care about results.",
    name: 'Ananya Patel',
    company: 'Founder, Spark Studio',
    initials: 'AP',
    color: '#58c6e9',
  },
]

const current = ref(0)
let autoplay

function next() {
  current.value = (current.value + 1) % testimonials.length
}
function prev() {
  current.value = (current.value - 1 + testimonials.length) % testimonials.length
}

onMounted(() => {
  autoplay = setInterval(next, 4000)
})
onUnmounted(() => {
  clearInterval(autoplay)
})
</script>
