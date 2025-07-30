<template>
  <section id="services" class="section bg-secondary">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Our Services</h2>
        <p class="section-subtitle">
          We offer comprehensive solutions to help your business thrive in the digital landscape
        </p>
      </div>

      <div class="services-grid">
        <div 
          v-for="service in services" 
          :key="service.id"
          class="service-card card"
          :class="{ 'animate-fade-in-up': isVisible }"
        >
          <div class="service-icon">
            <div class="icon-wrapper" :style="{ backgroundColor: service.color }">
              <span class="icon">{{ service.icon }}</span>
            </div>
          </div>
          <h3 class="service-title">{{ service.title }}</h3>
          <p class="service-description">{{ service.description }}</p>
          <ul class="service-features">
            <li v-for="feature in service.features" :key="feature">{{ feature }}</li>
          </ul>
          <a href="#contact" @click="scrollToContact" class="service-link">
            Learn More →
          </a>
        </div>
      </div>

      <!-- Call to Action -->
      <div class="cta-section">
        <div class="cta-content">
          <h3>Ready to Get Started?</h3>
          <p>Let's discuss how we can help transform your business</p>
          <a href="#contact" @click="scrollToContact" class="btn btn-primary btn-lg">
            Start Your Project
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { ref, onMounted } from 'vue'

export default {
  name: 'ServicesSection',
  setup() {
    const isVisible = ref(false)

    const services = [
      {
        id: 1,
        title: 'Web Development',
        description: 'Custom web applications built with modern technologies and best practices.',
        icon: '💻',
        color: '#3b82f6',
        features: [
          'Responsive Design',
          'Modern Frameworks',
          'Performance Optimization',
          'SEO Friendly'
        ]
      },
      {
        id: 2,
        title: 'Mobile Development',
        description: 'Native and cross-platform mobile applications for iOS and Android.',
        icon: '📱',
        color: '#10b981',
        features: [
          'Native iOS & Android',
          'Cross-platform Solutions',
          'App Store Optimization',
          'Push Notifications'
        ]
      },
      {
        id: 3,
        title: 'UI/UX Design',
        description: 'Beautiful and intuitive user interfaces that enhance user experience.',
        icon: '🎨',
        color: '#f59e0b',
        features: [
          'User Research',
          'Wireframing & Prototyping',
          'Visual Design',
          'Usability Testing'
        ]
      },
      {
        id: 4,
        title: 'Digital Marketing',
        description: 'Strategic digital marketing solutions to grow your online presence.',
        icon: '📈',
        color: '#ef4444',
        features: [
          'SEO & SEM',
          'Social Media Marketing',
          'Content Strategy',
          'Analytics & Reporting'
        ]
      },
      {
        id: 5,
        title: 'Cloud Solutions',
        description: 'Scalable cloud infrastructure and DevOps solutions for modern businesses.',
        icon: '☁️',
        color: '#8b5cf6',
        features: [
          'AWS/Azure/GCP',
          'CI/CD Pipelines',
          'Monitoring & Security',
          'Cost Optimization'
        ]
      },
      {
        id: 6,
        title: 'Consulting',
        description: 'Expert guidance to help you make informed technology decisions.',
        icon: '🤝',
        color: '#06b6d4',
        features: [
          'Technology Strategy',
          'Architecture Review',
          'Team Training',
          'Project Management'
        ]
      }
    ]

    const scrollToContact = () => {
      const element = document.getElementById('contact')
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' })
      }
    }

    onMounted(() => {
      // Trigger animation when component mounts
      setTimeout(() => {
        isVisible.value = true
      }, 100)
    })

    return {
      services,
      isVisible,
      scrollToContact
    }
  }
}
</script>

<style scoped>
.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: var(--spacing-8);
  margin-bottom: var(--spacing-16);
}

.service-card {
  padding: var(--spacing-8);
  text-align: center;
  transition: all var(--transition-normal);
  border: 1px solid var(--border-color);
  position: relative;
  overflow: hidden;
}

.service-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  transform: scaleX(0);
  transition: transform var(--transition-normal);
}

.service-card:hover::before {
  transform: scaleX(1);
}

.service-card:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-xl);
}

.service-icon {
  margin-bottom: var(--spacing-6);
}

.icon-wrapper {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto;
  position: relative;
  overflow: hidden;
}

.icon-wrapper::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  transform: scale(0);
  transition: transform var(--transition-normal);
}

.service-card:hover .icon-wrapper::before {
  transform: scale(1);
}

.icon {
  font-size: var(--font-size-3xl);
  z-index: 1;
  position: relative;
}

.service-title {
  font-size: var(--font-size-xl);
  font-weight: 600;
  margin-bottom: var(--spacing-4);
  color: var(--text-primary);
}

.service-description {
  color: var(--text-secondary);
  margin-bottom: var(--spacing-6);
  line-height: 1.6;
}

.service-features {
  list-style: none;
  margin-bottom: var(--spacing-6);
  text-align: left;
}

.service-features li {
  padding: var(--spacing-2) 0;
  color: var(--text-secondary);
  position: relative;
  padding-left: var(--spacing-6);
}

.service-features li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: var(--secondary-color);
  font-weight: bold;
}

.service-link {
  color: var(--primary-color);
  text-decoration: none;
  font-weight: 500;
  transition: color var(--transition-fast);
  display: inline-block;
}

.service-link:hover {
  color: var(--primary-dark);
  transform: translateX(4px);
}

.cta-section {
  background: var(--bg-primary);
  border-radius: var(--radius-2xl);
  padding: var(--spacing-12);
  text-align: center;
  box-shadow: var(--shadow-lg);
  margin-top: var(--spacing-16);
}

.cta-content h3 {
  font-size: var(--font-size-3xl);
  margin-bottom: var(--spacing-4);
  color: var(--text-primary);
}

.cta-content p {
  font-size: var(--font-size-lg);
  color: var(--text-secondary);
  margin-bottom: var(--spacing-8);
}

/* Responsive Design */
@media (max-width: 768px) {
  .services-grid {
    grid-template-columns: 1fr;
    gap: var(--spacing-6);
    margin-bottom: var(--spacing-12);
  }

  .service-card {
    padding: var(--spacing-6);
    margin-bottom: var(--spacing-4);
  }

  .service-features {
    margin-bottom: var(--spacing-4);
  }

  .service-features li {
    padding: var(--spacing-1) 0;
    padding-left: var(--spacing-4);
  }

  .cta-section {
    padding: var(--spacing-8);
    margin-top: var(--spacing-12);
  }

  .cta-content h3 {
    font-size: var(--font-size-2xl);
  }

  .cta-content p {
    font-size: var(--font-size-base);
  }
}

@media (max-width: 480px) {
  .services-grid {
    gap: var(--spacing-4);
  }

  .service-card {
    padding: var(--spacing-4);
  }

  .icon-wrapper {
    width: 60px;
    height: 60px;
  }

  .icon {
    font-size: var(--font-size-2xl);
  }

  .service-title {
    font-size: var(--font-size-lg);
  }

  .service-description {
    font-size: var(--font-size-sm);
  }

  .cta-section {
    padding: var(--spacing-6);
  }

  .cta-content h3 {
    font-size: var(--font-size-xl);
  }
}
</style> 