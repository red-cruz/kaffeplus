<template>
  <nav class="navbar bg-body-tertiary">
    <div class="container-fluid">
      <RouterLink to="/" class="nav-link me-3" active-class="active">
        <img :src="logo" alt="Kaffe+" width="70" />
      </RouterLink>

      <ul class="navbar-nav me-auto flex-row">
        <NavItem href="/order">
          <Icon icon="line-md:coffee-half-empty-twotone-loop" class="align-middle" width="20" />
          <span class="align-middle">Order <span class="d-none d-sm-inline">Now</span></span>
        </NavItem>

        <NavItem href="/about">
          <Icon icon="line-md:buy-me-a-coffee-twotone" width="20" />
          <span class="align-middle">About <span class="d-none d-sm-inline">Us</span></span>
        </NavItem>
      </ul>
      <a
        href="https://github.com/red-cruz"
        class="me-3"
        target="_blank"
        style="text-decoration: none; color: inherit"
      >
        <Icon icon="line-md:github-loop" width="21" />
      </a>
      <span class="me-3" role="button" data-bs-toggle="offcanvas" href="#offcanvasExample">
        <Icon icon="mdi:cart-outline" width="21" />
      </span>
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
