<template>
  <header class="bg-white shadow-lg sticky top-0 z-50">
    <nav class="container-custom">
      <div class="flex justify-between items-center py-4">
        <!-- Logo -->
        <router-link to="/" class="flex items-center space-x-3 group">
          <div
            class="w-10 h-10 bg-gradient-to-r from-primary-500 to-purple-600 rounded-lg flex items-center justify-center group-hover:scale-105 transition-transform"
          >
            <span class="text-white font-bold text-xl">T</span>
          </div>
          <span class="text-2xl font-bold text-gray-800">TechSolution</span>
        </router-link>

        <!-- Desktop Navigation -->
        <AppNavigation class="hidden lg:flex" />

        <!-- Mobile Menu Button -->
        <button
          @click="toggleMobileMenu"
          class="lg:hidden p-2 rounded-md text-gray-600 hover:text-primary-600 hover:bg-gray-100 transition-colors"
          aria-label="Toggle mobile menu"
        >
          <div class="w-6 h-6 flex flex-col justify-center items-center">
            <span
              class="w-6 h-0.5 bg-current transition-all duration-300"
              :class="{ 'rotate-45 translate-y-1.5': isMobileMenuOpen }"
            ></span>
            <span
              class="w-6 h-0.5 bg-current my-1 transition-all duration-300"
              :class="{ 'opacity-0': isMobileMenuOpen }"
            ></span>
            <span
              class="w-6 h-0.5 bg-current transition-all duration-300"
              :class="{ '-rotate-45 -translate-y-1.5': isMobileMenuOpen }"
            ></span>
          </div>
        </button>
      </div>

      <!-- Mobile Navigation -->
      <div v-show="isMobileMenuOpen" class="lg:hidden pb-4 border-t border-gray-100">
        <AppNavigation
          @link-clicked="closeMobileMenu"
          class="flex flex-col space-y-2 mt-4"
          mobile
        />
      </div>
    </nav>
  </header>
</template>

<script>
import { ref } from 'vue'
import AppNavigation from './AppNavigation.vue'

export default {
  name: 'AppHeader',
  components: {
    AppNavigation,
  },
  setup() {
    const isMobileMenuOpen = ref(false)

    const toggleMobileMenu = () => {
      isMobileMenuOpen.value = !isMobileMenuOpen.value
    }

    const closeMobileMenu = () => {
      isMobileMenuOpen.value = false
    }

    return {
      isMobileMenuOpen,
      toggleMobileMenu,
      closeMobileMenu,
    }
  },
}
</script>
