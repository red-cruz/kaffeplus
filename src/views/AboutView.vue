<template>
  <div class="container-fluid">
    <div class="row mt-3">
      <div class="col-12 col-md-6 col-lg-4 mb-3" v-for="person of persons" :key="person.name">
        <div class="card">
          <img :src="person.img" class="card-img-top" :alt="person.name" />
          <div class="card-body">
            <h5 class="card-title">{{ person.name }}</h5>
            <p class="card-text">
              {{ person.description }}
            </p>
            <a :href="person.link" class="btn btn-primary">Visit</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import chi from '../assets/img/chi.jpg'
import marie from '../assets/img/1chi.jpg'
const persons = [
  {
    img: chi,
    name: 'Taichi Aizawa',
    description: 'Ewan',
    link: 'link',
  },
  {
    img: marie,
    name: 'Marie Manarang',
    description: 'Ewan',
    link: 'link',
  },
]
</script>
<style></style>
