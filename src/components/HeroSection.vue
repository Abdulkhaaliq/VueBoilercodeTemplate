<template>
  <section id="home" class="hero-section">
    <!-- Parallax Background -->
    <div class="hero-background">
      <div class="parallax-layer parallax-bg" :style="{ transform: `translateY(${parallaxOffset}px)` }"></div>
      <div class="parallax-layer parallax-overlay"></div>
    </div>

    <!-- Hero Content -->
    <div class="container">
      <div class="hero-content">
        <div class="hero-text">
          <h1 class="hero-title animate-fade-in-up">
            Transform Your Business
            <span class="text-primary">With Innovation</span>
          </h1>
          <p class="hero-subtitle animate-fade-in-up">
            We help businesses grow and succeed in the digital age with cutting-edge solutions 
            and strategic expertise that drives real results.
          </p>
          <div class="hero-buttons animate-fade-in-up">
            <a href="#services" @click="scrollToSection('services')" class="btn btn-primary btn-lg">
              Explore Services
            </a>
            <a href="#contact" @click="scrollToSection('contact')" class="btn btn-secondary btn-lg">
              Get Started
            </a>
          </div>
        </div>

        <!-- Hero Stats -->
        <div class="hero-stats animate-fade-in-up">
          <div class="stat-item">
            <div class="stat-number">500+</div>
            <div class="stat-label">Happy Clients</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">1000+</div>
            <div class="stat-label">Projects Completed</div>
          </div>
          <div class="stat-item">
            <div class="stat-number">99%</div>
            <div class="stat-label">Success Rate</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll Indicator -->
    <div class="scroll-indicator">
      <div class="scroll-arrow"></div>
    </div>
  </section>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue'

export default {
  name: 'HeroSection',
  setup() {
    const parallaxOffset = ref(0)

    const handleScroll = () => {
      const scrolled = window.pageYOffset
      parallaxOffset.value = scrolled * 0.5
    }

    const scrollToSection = (sectionId) => {
      const element = document.getElementById(sectionId)
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' })
      }
    }

    onMounted(() => {
      window.addEventListener('scroll', handleScroll)
    })

    onUnmounted(() => {
      window.removeEventListener('scroll', handleScroll)
    })

    return {
      parallaxOffset,
      scrollToSection
    }
  }
}
</script>

<style scoped>
.hero-section {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
}

.hero-background {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: -1;
}

.parallax-layer {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.parallax-bg {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  background-size: 400% 400%;
  animation: gradientShift 15s ease infinite;
}

.parallax-overlay {
  background: rgba(0, 0, 0, 0.3);
}

@keyframes gradientShift {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: var(--spacing-16);
  align-items: center;
  padding: var(--spacing-20) 0;
}

.hero-text {
  color: white;
  max-width: 600px;
}

.hero-title {
  font-size: var(--font-size-6xl);
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: var(--spacing-6);
  animation-delay: 0.2s;
}

.hero-subtitle {
  font-size: var(--font-size-xl);
  line-height: 1.6;
  margin-bottom: var(--spacing-8);
  opacity: 0.9;
  animation-delay: 0.4s;
  color: white;
}

.hero-buttons {
  display: flex;
  gap: var(--spacing-4);
  animation-delay: 0.6s;
}

.hero-stats {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-8);
  color: white;
  animation-delay: 0.8s;
}

.stat-item {
  text-align: center;
  padding: var(--spacing-4);
  background: rgba(255, 255, 255, 0.1);
  border-radius: var(--radius-xl);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.stat-number {
  font-size: var(--font-size-3xl);
  font-weight: 700;
  color: var(--accent-color);
  margin-bottom: var(--spacing-2);
}

.stat-label {
  font-size: var(--font-size-sm);
  opacity: 0.8;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.scroll-indicator {
  position: absolute;
  bottom: var(--spacing-8);
  left: 50%;
  transform: translateX(-50%);
  color: white;
  animation: bounce 2s infinite;
}

.scroll-arrow {
  width: 2px;
  height: 30px;
  background: white;
  position: relative;
}

.scroll-arrow::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 0;
  border-left: 6px solid transparent;
  border-right: 6px solid transparent;
  border-top: 8px solid white;
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% {
    transform: translateX(-50%) translateY(0);
  }
  40% {
    transform: translateX(-50%) translateY(-10px);
  }
  60% {
    transform: translateX(-50%) translateY(-5px);
  }
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: var(--spacing-8);
    text-align: center;
    padding: var(--spacing-12) 0;
  }

  .hero-section {
    margin-top: 70px;
  }

  .hero-title {
    font-size: var(--font-size-4xl);
    margin-bottom: var(--spacing-4);
  }

  .hero-subtitle {
    font-size: var(--font-size-lg);
    margin-bottom: var(--spacing-6);
  }

  .hero-buttons {
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-3);
  }

  .hero-stats {
    flex-direction: row;
    justify-content: center;
    gap: var(--spacing-4);
    flex-wrap: wrap;
  }

  .stat-item {
    flex: 1;
    min-width: 100px;
    max-width: 120px;
  }

  .stat-number {
    font-size: var(--font-size-2xl);
  }

  .stat-label {
    font-size: var(--font-size-xs);
  }
}

@media (max-width: 480px) {
  .hero-content {
    padding: var(--spacing-8) 0;
  }

  .hero-title {
    font-size: var(--font-size-3xl);
  }

  .hero-subtitle {
    font-size: var(--font-size-base);
  }

  .hero-stats {
    flex-direction: column;
    gap: var(--spacing-3);
    width: 100%;
  }

  .stat-item {
    max-width: none;
    width: 100%;
  }

  .hero-buttons {
    width: 100%;
  }

  .hero-buttons .btn {
    width: 100%;
    justify-content: center;
  }
}
</style> 