<script setup>
const { title = 'Tombol', disabled = false } = defineProps({
  title: String,
})
</script>

<template>
  <button :disabled>{{ title }}</button>
</template>

<style scoped></style>
