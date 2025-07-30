<template>
  <footer class="bg-gray-900 text-white">
    <div class="container-custom section-padding">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <!-- Company Info -->
        <div class="space-y-4">
          <div class="flex items-center space-x-3">
            <div
              class="w-10 h-10 bg-gradient-to-r from-primary-500 to-purple-600 rounded-lg flex items-center justify-center"
            >
              <span class="text-white font-bold text-xl">T</span>
            </div>
            <span class="text-2xl font-bold">TechSolution</span>
          </div>
          <p class="text-gray-300 leading-relaxed">
            Menghadirkan solusi teknologi terdepan untuk transformasi digital bisnis Anda.
          </p>
          <div class="flex space-x-4">
            <a
              v-for="social in socialLinks"
              :key="social.name"
              :href="social.url"
              class="w-10 h-10 bg-gray-800 hover:bg-primary-600 rounded-lg flex items-center justify-center transition-colors"
              :aria-label="social.name"
            >
              <span class="text-lg">{{ social.icon }}</span>
            </a>
          </div>
        </div>

        <!-- Quick Links -->
        <div>
          <h3 class="text-lg font-semibold mb-4">Quick Links</h3>
          <ul class="space-y-2">
            <li v-for="item in navigationItems" :key="item.path">
              <router-link :to="item.path" class="text-gray-300 hover:text-white transition-colors">
                {{ item.name }}
              </router-link>
            </li>
          </ul>
        </div>

        <!-- Services -->
        <div>
          <h3 class="text-lg font-semibold mb-4">Layanan Kami</h3>
          <ul class="space-y-2">
            <li v-for="service in footerServices" :key="service">
              <span class="text-gray-300">{{ service }}</span>
            </li>
          </ul>
        </div>

        <!-- Contact Info -->
        <div>
          <h3 class="text-lg font-semibold mb-4">Kontak</h3>
          <div class="space-y-2">
            <div class="flex items-center space-x-2 text-gray-300">
              <span>📍</span>
              <span>Jakarta, Indonesia</span>
            </div>
            <div class="flex items-center space-x-2 text-gray-300">
              <span>📞</span>
              <span>+62 21 1234 5678</span>
            </div>
            <div class="flex items-center space-x-2 text-gray-300">
              <span>✉️</span>
              <span>info@techsolution.com</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Bottom Section -->
      <div
        class="border-t border-gray-800 mt-8 pt-8 flex flex-col md:flex-row justify-between items-center"
      >
        <p class="text-gray-400 text-sm">© {{ currentYear }} TechSolution. All rights reserved.</p>
        <div class="flex space-x-6 mt-4 md:mt-0">
          <a href="#" class="text-gray-400 hover:text-white text-sm transition-colors">
            Privacy Policy
          </a>
          <a href="#" class="text-gray-400 hover:text-white text-sm transition-colors">
            Terms of Service
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import { computed } from 'vue'
import { navigationItems } from '@/data/navigation.js'

export default {
  name: 'AppFooter',
  setup() {
    const currentYear = computed(() => new Date().getFullYear())

    const socialLinks = [
      { name: 'Facebook', icon: '📘', url: '#' },
      { name: 'Twitter', icon: '🐦', url: '#' },
      { name: 'LinkedIn', icon: '💼', url: '#' },
      { name: 'Instagram', icon: '📷', url: '#' },
    ]

    const footerServices = [
      'Web Development',
      'Mobile Apps',
      'Cloud Solutions',
      'Digital Marketing',
      'UI/UX Design',
    ]

    return {
      currentYear,
      navigationItems,
      socialLinks,
      footerServices,
    }
  },
}
</script>
