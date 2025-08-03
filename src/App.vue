<script setup>
const name = 'teguh bagmar'
</script>

<template>
  <h1 class="text-3xl text-red-500">Hellow world</h1>
  <MainButton :title="`submit`" />
  <MainButton :disabled="true" />
  <p>{{ name }}</p>
</template>

<style scoped></style>
