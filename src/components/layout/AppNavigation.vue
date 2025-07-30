<template>
  <nav :class="containerClass">
    <router-link
      v-for="item in navigationItems"
      :key="item.path"
      :to="item.path"
      @click="$emit('linkClicked')"
      class="nav-link"
      :class="navLinkClass"
      active-class="active"
    >
      <span class="mr-2">{{ item.icon }}</span>
      {{ item.name }}
    </router-link>
  </nav>
</template>

<script>
import { computed } from 'vue'
import { navigationItems } from '@/data/navigation.js'

export default {
  name: 'AppNavigation',
  props: {
    mobile: {
      type: Boolean,
      default: false,
    },
  },
  emits: ['linkClicked'],
  setup(props) {
    const containerClass = computed(() => {
      return props.mobile ? 'flex flex-col space-y-2' : 'flex items-center space-x-8'
    })

    const navLinkClass = computed(() => {
      return props.mobile
        ? 'text-gray-600 hover:text-primary-600 px-3 py-2 rounded-md font-medium transition-colors block'
        : 'text-gray-600 hover:text-primary-600 px-3 py-2 rounded-md font-medium transition-colors relative'
    })

    return {
      navigationItems,
      containerClass,
      navLinkClass,
    }
  },
}
</script>

<style scoped>
.nav-link.active {
  @apply text-primary-600 bg-primary-50;
}

.nav-link:not(.mobile)::after {
  content: '';
  position: absolute;
  bottom: -1px;
  left: 50%;
  width: 0;
  height: 2px;
  background-color: theme('colors.primary.600');
  transition: all 0.3s ease;
  transform: translateX(-50%);
}

.nav-link.active:not(.mobile)::after {
  width: 100%;
}
</style>
