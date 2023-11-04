<template>
  <div class="container-fluid">
    <div class="row mt-3">
      <div class="col-12 col-md-6 col-lg-4 mb-3" v-for="person of persons" :key="person.name">
        <div class="card">
          <img
            :src="person.img"
            class="card-img-top object-fit-cover"
            :alt="person.name"
            width="400"
            height="400"
          />
          <div class="card-body">
            <h5 class="card-title">{{ person.name }}</h5>
            <p class="card-text">
              {{ person.description }}
            </p>
            <a :href="person.link" target="_blank" class="btn btn-primary">Visit</a>
          </div>
        </div>
      </div>
    </div>
    <div class="text-center w-100">
      <h4 class="mt-4">We are located at</h4>
      <p>33 Melencio Street Extension , Cabanatuan City, Philippines, 3100</p>
      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3844.9221469128183!2d120.9671116!3d15.4886193!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x33972921a5ecdf7d%3A0x631e48463b3b76c2!2sFreshaire%20Hair%20Strengthening%20Center!5e0!3m2!1sen!2sph!4v1699114459156!5m2!1sen!2sph"
        :width="width"
        height="600"
        style="border: 0"
        allowfullscreen=""
        loading="lazy"
        referrerpolicy="no-referrer-when-downgrade"
      ></iframe>
    </div>
  </div>
</template>

<script setup>
import chi from '../assets/img/chi.jpg'
import marie from '../assets/img/1chi.jpg'
import { onMounted } from 'vue'
import anime from 'animejs'

const width = window.screen.width > 800 ? 800 : window.screen.width
const persons = [
  {
    img: chi,
    name: 'Taichi Aizawa',
    description: `
      Taichi Aizawa, founder of Kaffe Plus,
      is a young entrepreneur who is passionate about providing his customers with a high-quality coffee experience.
      He uses only the freshest ingredients and the most skilled baristas to create his delicious drinks,
      and he offers a variety of brewing methods so you can find the perfect cup of coffee to your taste.
      Taichi is also committed to creating a comfortable and inviting atmosphere for his customers,
      and he invites you to come and experience the Kaffe Plus difference today.
    `,
    link: 'https://web.facebook.com/xMatrixKirigawax',
  },
  {
    img: marie,
    name: 'Marie Manarang',
    description: 'asfasfsfs',
    link: 'https://web.facebook.com/xMatrixKirigawax',
  },
  {
    img: chi,
    name: 'Person idk',
    description: 'asfasfsfs',
    link: 'https://web.facebook.com/xMatrixKirigawax',
  },
]

onMounted(() => {
  anime({
    targets: ['img', ''],
    scale: [0, 1],
    duration: 1500,
    elasticity: 600,
    delay: (el, i) => 45 * (i + 1),
  })
})
</script>
<style></style>
