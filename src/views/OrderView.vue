<template>
  <div class="container-fluid">
    <p class="text-danger">product catalog dito SIGURO</p>

    <form method="post" class="mt-2" id="order" action="" novalidate>
      <div class="form-floating mb-3">
        <input type="text" class="form-control" id="name" placeholder="" />
        <label for="name">Name</label>
      </div>
      <button type="submit" class="btn btn-primary">Add to cart</button>
    </form>
  </div>
</template>

<script setup>
import Swal from 'sweetalert2'
import Vts from 'vts.js'
import { onMounted } from 'vue'

onMounted(() => {
  const vts = new Vts('order', { halt: true })
  vts.form.addEventListener('submit', () => {
    Swal.fire({
      title: 'Na-add na sa cart',
      icon: 'success',
    })
  })
})
</script>

<style lang="scss" scoped></style>
