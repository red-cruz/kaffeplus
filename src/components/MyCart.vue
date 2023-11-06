<template>
  <div
    class="offcanvas offcanvas-start"
    tabindex="-1"
    id="offcanvasExample"
    aria-labelledby="offcanvasExampleLabel"
  >
    <div class="offcanvas-header">
      <h5 class="offcanvas-title" id="offcanvasExampleLabel">
        My Cart <span class="badge text-bg-secondary">3</span>
      </h5>
      <button
        type="button"
        class="btn-close"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body">
      <div class="card mb-1" style="max-width: 540px" v-for="i of 3" :key="i">
        <div class="row g-0">
          <img :src="chi" class="img-fluid rounded-start col-3 object-fit-cover" alt="..." />
          <div class="col-md-9">
            <div class="card-body">
              <h6 class="card-title">Milk Tea</h6>
              <p class="card-text">with toppings idk</p>
              <p class="card-text">
                <small class="text-body-secondary">Last updated 3 mins ago</small>
              </p>
            </div>
          </div>
        </div>
      </div>

      <button class="btn btn-primary mt-3" @click="order">Place order</button>
    </div>
  </div>
</template>

<script setup>
import Swal from 'sweetalert2'
import chi from '../assets/img/chi.jpg'

function order() {
  Swal.fire({
    icon: 'info',
    title: 'Order placed!',
    text: 'We will prepare your order ASAP.',
  })
}
</script>

<style lang="scss" scoped></style>
