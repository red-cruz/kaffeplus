<template>
  <nav class="navbar bg-body-tertiary">
    <div class="container-fluid">
      <RouterLink to="/" class="nav-link me-3" active-class="active">
        <img :src="logo" alt="Kaffe+" width="70" />
      </RouterLink>

      <ul class="navbar-nav me-auto flex-row">
        <NavItem href="/about">
          <Icon icon="line-md:coffee-half-empty-twotone-loop" width="20" />
          <span> Order Now</span>
        </NavItem>
        <NavItem href="/about">
          <Icon icon="line-md:question-circle" width="20" />
          About <span class="d-none d-sm-inline">Us</span>
        </NavItem>
      </ul>
      <ThemeToggle @dark="logo = light" @light="logo = dark" />
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
import dark from '../assets/img/logo-dark.png'
import light from '../assets/img/logo-light.png'
import ThemeToggle from './ThemeToggle.vue'
import NavItem from './NavItem.vue'
import { Icon } from '@iconify/vue'
import { RouterLink } from 'vue-router'

const logo = ref(dark)
</script>

<style lang="scss" scoped></style>
