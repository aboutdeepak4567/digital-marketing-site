<template>
  <section id="contact" class="contact-section">
    <div class="container contact-container">

      <!-- Info Panel -->
      <div class="contact-info fade-in">
        <span class="section-badge">Get In Touch</span>
        <h2>Let's Build Something <span class="accent">Great</span></h2>
        <p>Have a project in mind? Fill out the form and we'll get back to you within 24 hours.</p>

        <div class="contact-details">
          <div class="contact-item">
            <span class="contact-icon">📧</span>
            <span>hello@creativeagency.co</span>
          </div>
          <div class="contact-item">
            <span class="contact-icon">📞</span>
            <span>+1 (555) 012-3456</span>
          </div>
          <div class="contact-item">
            <span class="contact-icon">📍</span>
            <span>123 Design Street, San Francisco, CA</span>
          </div>
        </div>

        <div class="contact-socials">
          <a href="#" aria-label="LinkedIn" class="social-icon">in</a>
          <a href="#" aria-label="Twitter" class="social-icon">𝕏</a>
          <a href="#" aria-label="Instagram" class="social-icon">ig</a>
          <a href="#" aria-label="GitHub" class="social-icon">gh</a>
        </div>
      </div>

      <!-- Form -->
      <div class="contact-form-wrapper fade-in">
        <form class="contact-form" @submit.prevent="handleSubmit" novalidate>

          <div class="form-group">
            <label for="name">Full Name</label>
            <input
              id="name"
              v-model.trim="form.name"
              type="text"
              placeholder="Jane Smith"
              :class="{ error: errors.name }"
            />
            <span v-if="errors.name" class="error-msg">{{ errors.name }}</span>
          </div>

          <div class="form-group">
            <label for="email">Email Address</label>
            <input
              id="email"
              v-model.trim="form.email"
              type="email"
              placeholder="jane@example.com"
              :class="{ error: errors.email }"
            />
            <span v-if="errors.email" class="error-msg">{{ errors.email }}</span>
          </div>

          <div class="form-group">
            <label for="subject">Subject</label>
            <select id="subject" v-model="form.subject" :class="{ error: errors.subject }">
              <option value="">— Select a topic —</option>
              <option>Brand Design</option>
              <option>Web Development</option>
              <option>Social Media</option>
              <option>Digital Advertising</option>
              <option>General Enquiry</option>
            </select>
            <span v-if="errors.subject" class="error-msg">{{ errors.subject }}</span>
          </div>

          <div class="form-group">
            <label for="message">Message</label>
            <textarea
              id="message"
              v-model.trim="form.message"
              rows="5"
              placeholder="Tell us about your project..."
              :class="{ error: errors.message }"
            ></textarea>
            <span v-if="errors.message" class="error-msg">{{ errors.message }}</span>
          </div>

          <button type="submit" class="primary-button submit-btn" :disabled="submitted">
            {{ submitted ? '✓ Message Sent!' : 'Send Message' }}
          </button>

          <div v-if="submitted" class="success-toast">
            🎉 Thanks! We'll be in touch within 24 hours.
          </div>

        </form>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'

const form = reactive({ name: '', email: '', subject: '', message: '' })
const errors = reactive({ name: '', email: '', subject: '', message: '' })
const submitted = ref(false)

function validate() {
  let valid = true
  errors.name = form.name ? '' : 'Full name is required.'
  if (errors.name) valid = false

  if (!form.email) {
    errors.email = 'Email address is required.'
    valid = false
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)) {
    errors.email = 'Please enter a valid email.'
    valid = false
  } else {
    errors.email = ''
  }

  errors.subject = form.subject ? '' : 'Please select a subject.'
  if (errors.subject) valid = false

  errors.message = form.message.length >= 10 ? '' : 'Message must be at least 10 characters.'
  if (errors.message) valid = false

  return valid
}

function handleSubmit() {
  if (!validate()) return
  // Simulate async send
  submitted.value = true
  setTimeout(() => {
    Object.assign(form, { name: '', email: '', subject: '', message: '' })
    submitted.value = false
  }, 5000)
}
</script>
