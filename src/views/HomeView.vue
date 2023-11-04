<template>
  <div>
    <HomeCarousel />
    <div class="text-center w-100">
      <h1 class="mt-4">Follow us on Facebook</h1>
      <iframe
        :src="fbSrc"
        :width="width"
        height="700"
        style="border: none; overflow: hidden"
        scrolling="no"
        frameborder="0"
        allowfullscreen="true"
        allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"
      ></iframe>
    </div>
  </div>
</template>

<script setup>
import HomeCarousel from '../components/HomeCarousel.vue'

const width = window.screen.width > 500 ? 500 : window.screen.width
const fbSrc =
  'https://www.facebook.com/plugins/page.php?href=https%3A%2F%2Fweb.facebook.com%2Fkaffeplus&tabs=timeline' +
  `&width=${width}px` +
  `&height=700px` +
  '&small_header=false' +
  '&adapt_container_width=true' +
  '&hide_cover=false' +
  '&show_facepile=true' +
  '&appId'
</script>

<style lang="scss" scoped></style>
