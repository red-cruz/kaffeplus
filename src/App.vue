<template>
  <NavBar />
  <main>
    <RouterView />
  </main>
  <MyCart />
</template>

<script setup>
import { RouterView } from 'vue-router'
import NavBar from './layouts/NavBar.vue'
import MyCart from './components/MyCart.vue'
</script>

<style lang="scss" scoped></style>
