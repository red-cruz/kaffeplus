<template>
  <div
    @click="switchTheme(preferredTheme === 'dark' ? 'light' : 'dark')"
    role="button"
  >
    <Icon
      v-if="preferredTheme === 'light'"
      icon="line-md:sunny-outline-to-moon-alt-loop-transition"
      width="25"
    >
    </Icon>
    <Icon
      v-else
      width="25"
      icon="line-md:moon-to-sunny-outline-loop-transition"
    />
  </div>
</template>

<script setup>
import { Icon } from '@iconify/vue';
import { onMounted, ref } from 'vue';

const emits = defineEmits(['dark', 'light']);
const prefersDarkMode = window.matchMedia('(prefers-color-scheme: dark)');
const preferredTheme = ref(localStorage.getItem('theme') || getTheme());

onMounted(() => {
  // Initial theme switch
  switchTheme(preferredTheme.value);
});

// theme change event listener
prefersDarkMode.addEventListener('change', () => {
  switchTheme(getTheme());
});

function getTheme() {
  return prefersDarkMode.matches ? 'dark' : 'light';
}

function switchTheme(theme) {
  const body = document.querySelector('body');
  body?.setAttribute('data-bs-theme', theme);
  localStorage.setItem('theme', theme);
  preferredTheme.value = theme;

  // switch theme for swal
  const swalLinkId = 'swal2-dark-theme-link';
  const swalLink = document.getElementById(swalLinkId);
  if (!swalLink) {
    const darkSwal = document.createElement('link');
    darkSwal.id = swalLinkId;
    darkSwal.rel = 'stylesheet';
    darkSwal.href = '/css/@sweetalert2_theme-dark.min.css';
    document.body.append(darkSwal);
  }
  if (theme === 'light') {
    // remove swal dark theme
    document.getElementById(swalLinkId)?.remove();
    emits('light');
  } else {
    emits('dark');
  }
}
</script>

<style lang="scss" scoped></style>
