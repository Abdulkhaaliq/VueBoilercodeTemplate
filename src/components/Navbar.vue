<template>
  <nav class="navbar" :class="{ 'navbar-scrolled': isScrolled }">
    <div class="container">
      <div class="navbar-content">
        <!-- Logo -->
        <div class="navbar-logo">
          <a href="#home" @click="scrollToSection('home')">
            <span class="logo-text">Brand</span>
          </a>
        </div>

        <!-- Desktop Navigation -->
        <div class="navbar-nav desktop-nav" :class="{ 'nav-hidden': isMobileMenuOpen }">
          <a 
            v-for="item in navItems" 
            :key="item.id"
            :href="`#${item.id}`"
            @click="scrollToSection(item.id)"
            class="nav-link"
            :class="{ 'active': activeSection === item.id }"
          >
            {{ item.label }}
          </a>
        </div>

        <!-- Mobile Menu Button -->
        <button 
          class="mobile-menu-btn"
          @click="toggleMobileMenu"
          :class="{ 'active': isMobileMenuOpen }"
        >
          <span class="hamburger-line"></span>
          <span class="hamburger-line"></span>
          <span class="hamburger-line"></span>
        </button>
      </div>

      <!-- Mobile Navigation -->
      <div class="mobile-nav" :class="{ 'mobile-nav-open': isMobileMenuOpen }">
        <a 
          v-for="item in navItems" 
          :key="item.id"
          :href="`#${item.id}`"
          @click="scrollToSection(item.id); closeMobileMenu()"
          class="mobile-nav-link"
          :class="{ 'active': activeSection === item.id }"
        >
          {{ item.label }}
        </a>
      </div>
    </div>
  </nav>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue'

export default {
  name: 'Navbar',
  setup() {
    const isScrolled = ref(false)
    const isMobileMenuOpen = ref(false)
    const activeSection = ref('home')

    const navItems = [
      { id: 'home', label: 'Home' },
      { id: 'services', label: 'Services' },
      { id: 'contact', label: 'Contact' }
    ]

    const handleScroll = () => {
      isScrolled.value = window.scrollY > 50
      
      // Update active section based on scroll position
      const sections = navItems.map(item => item.id)
      const scrollPosition = window.scrollY + 100

      for (let i = sections.length - 1; i >= 0; i--) {
        const section = document.getElementById(sections[i])
        if (section && section.offsetTop <= scrollPosition) {
          activeSection.value = sections[i]
          break
        }
      }
    }

    const scrollToSection = (sectionId) => {
      const element = document.getElementById(sectionId)
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' })
      }
    }

    const toggleMobileMenu = () => {
      isMobileMenuOpen.value = !isMobileMenuOpen.value
      document.body.style.overflow = isMobileMenuOpen.value ? 'hidden' : ''
    }

    const closeMobileMenu = () => {
      isMobileMenuOpen.value = false
      document.body.style.overflow = ''
    }

    onMounted(() => {
      window.addEventListener('scroll', handleScroll)
      handleScroll() // Initial check
    })

    onUnmounted(() => {
      window.removeEventListener('scroll', handleScroll)
      document.body.style.overflow = ''
    })

    return {
      isScrolled,
      isMobileMenuOpen,
      activeSection,
      navItems,
      scrollToSection,
      toggleMobileMenu,
      closeMobileMenu
    }
  }
}
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid var(--border-color);
  transition: all var(--transition-normal);
}

.navbar-scrolled {
  background: rgba(255, 255, 255, 0.98);
  box-shadow: var(--shadow-md);
}

.navbar-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--spacing-4) 0;
}

.navbar-logo .logo-text {
  font-size: var(--font-size-xl);
  font-weight: 700;
  color: var(--primary-color);
  text-decoration: none;
}

.desktop-nav {
  display: flex;
  gap: var(--spacing-8);
}

.nav-link {
  color: var(--text-primary);
  text-decoration: none;
  font-weight: 500;
  transition: color var(--transition-fast);
  position: relative;
}

.nav-link:hover,
.nav-link.active {
  color: var(--primary-color);
}

.nav-link.active::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  right: 0;
  height: 2px;
  background: var(--primary-color);
  border-radius: 1px;
}

.mobile-menu-btn {
  display: none;
  flex-direction: column;
  background: none;
  border: none;
  cursor: pointer;
  padding: var(--spacing-2);
  gap: 4px;
}

.hamburger-line {
  width: 24px;
  height: 2px;
  background: var(--text-primary);
  transition: all var(--transition-fast);
  border-radius: 1px;
}

.mobile-menu-btn.active .hamburger-line:nth-child(1) {
  transform: rotate(45deg) translate(6px, 6px);
}

.mobile-menu-btn.active .hamburger-line:nth-child(2) {
  opacity: 0;
}

.mobile-menu-btn.active .hamburger-line:nth-child(3) {
  transform: rotate(-45deg) translate(6px, -6px);
}

.mobile-nav {
  display: none;
  flex-direction: column;
  gap: var(--spacing-4);
  padding: var(--spacing-4) 0;
  border-top: 1px solid var(--border-color);
  background: var(--bg-primary);
  transform: translateY(-100%);
  opacity: 0;
  transition: all var(--transition-normal);
}

.mobile-nav-open {
  display: flex;
  transform: translateY(0);
  opacity: 1;
}

.mobile-nav-link {
  color: var(--text-primary);
  text-decoration: none;
  font-weight: 500;
  padding: var(--spacing-3) 0;
  transition: color var(--transition-fast);
}

.mobile-nav-link:hover,
.mobile-nav-link.active {
  color: var(--primary-color);
}

/* Responsive Design */
@media (max-width: 768px) {
  /* Remove margin-top from .navbar so it always sticks to the top */
  .navbar {
    margin-top: 0;
  }
  .desktop-nav {
    display: none;
  }

  .mobile-menu-btn {
    display: flex;
  }

  /* Remove display:flex from .mobile-nav here */
}
</style> 