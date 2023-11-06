<template>
  <div id="carousel" class="carousel slide carousel-dark border-bottom" data-bs-ride="carousel">
    <div class="carousel-indicators">
      <button
        v-for="(banner, index) in banners"
        :key="index"
        type="button"
        data-bs-target="#carousel"
        :data-bs-slide-to="index"
        :class="{ active: index === 0 }"
        :aria-current="{ active: index === 0 }"
        :aria-label="'Slide' + index + 1"
      ></button>
    </div>

    <div class="carousel-inner">
      <div
        class="carousel-item"
        v-for="(banner, index) in banners"
        :key="index"
        :class="{ active: index === 0 }"
      >
        <img :src="banner" class="d-block w-100" alt="..." />
      </div>
    </div>

    <button
      class="carousel-control-prev"
      type="button"
      data-bs-target="#carousel"
      data-bs-slide="prev"
    >
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button
      class="carousel-control-next"
      type="button"
      data-bs-target="#carousel"
      data-bs-slide="next"
    >
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>
</template>

<script setup>
import banner from '../assets/img/banner.png'
import bmilktea from '../assets/img/banner-milktea.png'
import bfrap from '../assets/img/banner-frappuccino.png'
import { onMounted } from 'vue'
import Carousel from 'bootstrap/js/dist/carousel'

const banners = [banner, bmilktea, bfrap]
onMounted(() => {
  Carousel.getOrCreateInstance('#carousel')
})
</script>

<style lang="scss" scoped></style>
