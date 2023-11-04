<template>
  <NavBar />
  <main>
    <RouterView />
  </main>
</template>

<script setup>
import { RouterView } from 'vue-router'
import NavBar from './layouts/NavBar.vue'
</script>

<style lang="scss" scoped></style>
