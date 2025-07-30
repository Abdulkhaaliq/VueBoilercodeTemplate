<template>
  <section id="contact" class="section bg-dark">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title text-white">Get In Touch</h2>
        <p class="section-subtitle text-white">
          Ready to start your next project? Let's discuss how we can help you achieve your goals.
        </p>
      </div>

      <div class="contact-content">
        <!-- Contact Information -->
        <div class="contact-info">
          <h3 class="contact-info-title">Contact Information</h3>
          <p class="contact-info-description">
            Reach out to us through any of these channels. We're here to help you succeed.
          </p>

          <div class="contact-methods">
            <div class="contact-method">
              <div class="contact-icon">
                <span>📧</span>
              </div>
              <div class="contact-details">
                <h4>Email</h4>
                <p>hello@company.com</p>
                <p>support@company.com</p>
              </div>
            </div>

            <div class="contact-method">
              <div class="contact-icon">
                <span>📞</span>
              </div>
              <div class="contact-details">
                <h4>Phone</h4>
                <p>+1 (555) 123-4567</p>
                <p>+1 (555) 987-6543</p>
              </div>
            </div>

            <div class="contact-method">
              <div class="contact-icon">
                <span>📍</span>
              </div>
              <div class="contact-details">
                <h4>Office</h4>
                <p>123 Business Street</p>
                <p>New York, NY 10001</p>
              </div>
            </div>

            <div class="contact-method">
              <div class="contact-icon">
                <span>⏰</span>
              </div>
              <div class="contact-details">
                <h4>Business Hours</h4>
                <p>Monday - Friday: 9AM - 6PM</p>
                <p>Saturday: 10AM - 4PM</p>
              </div>
            </div>
          </div>

          <!-- Social Media -->
          <div class="social-links">
            <h4>Follow Us</h4>
            <div class="social-icons">
              <a href="#" class="social-icon" title="LinkedIn">
                <span>💼</span>
              </a>
              <a href="#" class="social-icon" title="Twitter">
                <span>🐦</span>
              </a>
              <a href="#" class="social-icon" title="Facebook">
                <span>📘</span>
              </a>
              <a href="#" class="social-icon" title="Instagram">
                <span>📷</span>
              </a>
            </div>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="contact-form-container">
          <form @submit.prevent="handleSubmit" class="contact-form">
            <h3 class="form-title">Send us a Message</h3>
            
            <div class="form-group">
              <label for="name" class="form-label">Full Name *</label>
              <input
                id="name"
                v-model="formData.name"
                type="text"
                class="form-input"
                :class="{ 'error': errors.name }"
                placeholder="Enter your full name"
                required
              />
              <span v-if="errors.name" class="error-message">{{ errors.name }}</span>
            </div>

            <div class="form-group">
              <label for="email" class="form-label">Email Address *</label>
              <input
                id="email"
                v-model="formData.email"
                type="email"
                class="form-input"
                :class="{ 'error': errors.email }"
                placeholder="Enter your email address"
                required
              />
              <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
            </div>

            <div class="form-group">
              <label for="phone" class="form-label">Phone Number</label>
              <input
                id="phone"
                v-model="formData.phone"
                type="tel"
                class="form-input"
                placeholder="Enter your phone number"
              />
            </div>

            <div class="form-group">
              <label for="service" class="form-label">Service Interest</label>
              <select
                id="service"
                v-model="formData.service"
                class="form-input"
              >
                <option value="">Select a service</option>
                <option value="web-development">Web Development</option>
                <option value="mobile-development">Mobile Development</option>
                <option value="ui-ux-design">UI/UX Design</option>
                <option value="digital-marketing">Digital Marketing</option>
                <option value="cloud-solutions">Cloud Solutions</option>
                <option value="consulting">Consulting</option>
              </select>
            </div>

            <div class="form-group">
              <label for="message" class="form-label">Message *</label>
              <textarea
                id="message"
                v-model="formData.message"
                class="form-input form-textarea"
                :class="{ 'error': errors.message }"
                placeholder="Tell us about your project or inquiry"
                rows="5"
                required
              ></textarea>
              <span v-if="errors.message" class="error-message">{{ errors.message }}</span>
            </div>

            <button type="submit" class="btn btn-primary btn-lg form-submit" :disabled="isSubmitting">
              {{ isSubmitting ? 'Sending...' : 'Send Message' }}
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { ref, reactive } from 'vue'

export default {
  name: 'ContactSection',
  setup() {
    const isSubmitting = ref(false)
    const errors = reactive({})

    const formData = reactive({
      name: '',
      email: '',
      phone: '',
      service: '',
      message: ''
    })

    const validateForm = () => {
      errors.name = ''
      errors.email = ''
      errors.message = ''

      if (!formData.name.trim()) {
        errors.name = 'Name is required'
      }

      if (!formData.email.trim()) {
        errors.email = 'Email is required'
      } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.email)) {
        errors.email = 'Please enter a valid email address'
      }

      if (!formData.message.trim()) {
        errors.message = 'Message is required'
      }

      return Object.keys(errors).length === 0 || errors.name === '' && errors.email === '' && errors.message === ''
    }

    const handleSubmit = async () => {
      if (!validateForm()) {
        return
      }

      isSubmitting.value = true

      try {
        // Simulate API call
        await new Promise(resolve => setTimeout(resolve, 2000))
        
        // Reset form
        Object.keys(formData).forEach(key => {
          formData[key] = ''
        })
        
        alert('Thank you for your message! We\'ll get back to you soon.')
      } catch (error) {
        alert('Sorry, there was an error sending your message. Please try again.')
      } finally {
        isSubmitting.value = false
      }
    }

    return {
      formData,
      errors,
      isSubmitting,
      handleSubmit
    }
  }
}
</script>

<style scoped>
.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-16);
  align-items: start;
}

.contact-info {
  color: white;
}

.contact-info-title {
  font-size: var(--font-size-2xl);
  margin-bottom: var(--spacing-4);
}

.contact-info-description {
  color: rgba(255, 255, 255, 0.8);
  margin-bottom: var(--spacing-8);
  line-height: 1.6;
}

.contact-methods {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-6);
  margin-bottom: var(--spacing-8);
}

.contact-method {
  display: flex;
  align-items: flex-start;
  gap: var(--spacing-4);
}

.contact-icon {
  width: 50px;
  height: 50px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: var(--font-size-xl);
  flex-shrink: 0;
}

.contact-details h4 {
  font-size: var(--font-size-lg);
  margin-bottom: var(--spacing-2);
  color: white;
}

.contact-details p {
  color: rgba(255, 255, 255, 0.8);
  margin-bottom: var(--spacing-1);
  font-size: var(--font-size-sm);
}

.social-links {
  margin-top: var(--spacing-8);
}

.social-links h4 {
  margin-bottom: var(--spacing-4);
  color: white;
}

.social-icons {
  display: flex;
  gap: var(--spacing-4);
}

.social-icon {
  width: 45px;
  height: 45px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  transition: all var(--transition-fast);
  font-size: var(--font-size-lg);
}

.social-icon:hover {
  background: var(--primary-color);
  transform: translateY(-2px);
}

.contact-form-container {
  background: rgba(255, 255, 255, 0.05);
  border-radius: var(--radius-2xl);
  padding: var(--spacing-8);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.contact-form {
  color: white;
}

.form-title {
  font-size: var(--font-size-2xl);
  margin-bottom: var(--spacing-6);
  text-align: center;
}

.form-group {
  margin-bottom: var(--spacing-6);
}

.form-label {
  display: block;
  margin-bottom: var(--spacing-2);
  font-weight: 500;
  color: white;
}

.form-input,
.form-textarea {
  width: 100%;
  padding: var(--spacing-3) var(--spacing-4);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: var(--radius-lg);
  background: rgba(255, 255, 255, 0.1);
  color: white;
  font-size: var(--font-size-base);
  transition: all var(--transition-fast);
}

.form-input::placeholder,
.form-textarea::placeholder {
  color: rgba(255, 255, 255, 0.6);
}

.form-input:focus,
.form-textarea:focus {
  outline: none;
  border-color: var(--primary-color);
  background: rgba(255, 255, 255, 0.15);
}

.form-input.error,
.form-textarea.error {
  border-color: #ef4444;
}

.error-message {
  color: #ef4444;
  font-size: var(--font-size-sm);
  margin-top: var(--spacing-1);
  display: block;
}

.form-submit {
  width: 100%;
  margin-top: var(--spacing-4);
}

.form-submit:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

/* Responsive Design */
@media (max-width: 768px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: var(--spacing-8);
  }

  .contact-form-container {
    padding: var(--spacing-6);
  }

  .contact-methods {
    gap: var(--spacing-4);
  }

  .contact-method {
    gap: var(--spacing-3);
  }

  .contact-icon {
    width: 40px;
    height: 40px;
    font-size: var(--font-size-lg);
  }
}

@media (max-width: 480px) {
  .contact-form-container {
    padding: var(--spacing-4);
  }

  .form-title {
    font-size: var(--font-size-xl);
  }

  .contact-info-title {
    font-size: var(--font-size-xl);
  }
}
</style> 