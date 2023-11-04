<template>
  <div>
    <HomeCarousel />
    <div class="container-fluid">
      <h3 class="mt-4">
        Kaffe Plus: <small class="text-body-secondary">A New Coffee Shop Experience</small>
      </h3>
      <p>
        Kaffe Plus is a new coffee shop that is committed to providing its customers with a
        high-quality experience. We use only the freshest ingredients and the most skilled baristas
        to create our delicious drinks.
      </p>

      <p>
        We also offer a variety of brewing methods, so you can find the perfect cup of coffee to
        your taste. At Kaffe Plus, we believe that coffee is more than just a drink. It's a way to
        connect with others and start the day off right. That's why we've created a comfortable and
        inviting atmosphere where you can relax and enjoy your coffee.
      </p>

      <p>
        We invite you to come and experience the Kaffe Plus difference today. We're confident that
        you'll love our coffee, our service, and our atmosphere.
      </p>
    </div>
    <div class="text-center w-100">
      <h4 class="mt-4">Follow us on Facebook</h4>
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
import { onMounted } from 'vue'
import anime from 'animejs'

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

onMounted(() => {
  anime({
    targets: 'img',
    scale: [0, 1],
    duration: 1500,
    elasticity: 600,
    delay: (el, i) => 45 * (i + 1),
  })
})
</script>

<style lang="scss" scoped></style>
