<template>
  <li class="nav-item">
    <RouterLink :to="href" class="nav-link me-3" active-class="active">
      <slot></slot>
    </RouterLink>
  </li>
</template>

<script setup>
defineProps({
  href: {
    type: [Object, String],
    required: true,
  },
})
</script>

<style lang="scss" scoped></style>
