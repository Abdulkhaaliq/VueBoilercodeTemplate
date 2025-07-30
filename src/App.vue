<template>
  <div id="app">
    <Navbar />
    <HeroSection />
    <ServicesSection />
    <ContactSection />
    <footer class="footer">
      <div class="container text-center">
        Made by <span class="text-primary">Brand</span> &copy; {{ new Date().getFullYear() }}
      </div>
    </footer>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
import HeroSection from '@/components/HeroSection.vue'
import ServicesSection from '@/components/ServicesSection.vue'
import ContactSection from '@/components/ContactSection.vue'

export default {
  name: 'App',
  components: {
    Navbar,
    HeroSection,
    ServicesSection,
    ContactSection
  }
}
</script>

<style>
.footer {
  padding: 2rem 0;
  background: var(--bg-secondary);
  color: var(--text-secondary);
  font-size: 1rem;
  margin-top: 2rem;
}
</style> 