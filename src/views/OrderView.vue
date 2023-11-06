<template>
  <div class="container-fluid">
    <h2 class="text-center">MILK TEA</h2>

    <div class="row">
      <div class="col-12 col-md-6 mb-3">
        <div class="card">
          <div class="row g-0">
            <div class="col-md-4">
              <img
                :src="logo"
                class="card-img-top object-fit-cover"
                alt="..."
                style="max-height: 25vh"
              />
            </div>
            <div class="col-md-8">
              <div class="card-body">
                <h5 class="card-title">Dark Chocolate</h5>
                <p class="card-text text-primary">Milk tea</p>
                <div class="d-flex justify-content-between">
                  <strong class="fs-2">₱45</strong>
                  <div class="quantity-control input-group">
                    <button class="btn btn-sm" type="button">
                      <Icon icon="line-md:minus" width="22" />
                    </button>
                    <output class="form-control text-center fs-5" value="1" />
                    <button class="btn btn-sm" type="button">
                      <Icon icon="line-md:plus" width="22" />
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <form method="post" class="mt-2" id="order" action="" novalidate>
      <div class="form-floating mb-3">
        <input type="text" class="form-control" id="name" placeholder="" />
        <label for="name">Name</label>
      </div>
      <button type="submit" class="btn btn-primary">Add to cart</button>
    </form>

    <button type="button" class="btn btn-primary mt-3 me-3" @click="toPDF">
      gawa pdf resibo idk
    </button>
    <button type="button" class="btn btn-primary mt-3 me-3" @click="toQR">gawa qr code</button>
    <button v-show="show" type="button" class="btn btn-primary mt-3" @click="toQRDL">
      download qr code
    </button>

    <div class="m-3" id="canvas"></div>

    <p class="text-danger mt-5">kunwari eto yung order</p>
    <table id="order-table" class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">First</th>
          <th scope="col">Last</th>
          <th scope="col">Handle</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">1</th>
          <td>Mark</td>
          <td>Otto</td>
          <td>@mdo</td>
        </tr>
        <tr>
          <th scope="row">2</th>
          <td>Jacob</td>
          <td>Thornton</td>
          <td>@fat</td>
        </tr>
        <tr>
          <th scope="row">3</th>
          <td colspan="2">Larry the Bird</td>
          <td>@twitter</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import logo from '../assets/img/promo.jpg'
import Swal from 'sweetalert2'
import Vts from 'vts.js'
import { onMounted, ref } from 'vue'
import jsPDF from 'jspdf'
import autoTable from 'jspdf-autotable'
import QRCodeStyling from 'qr-code-styling'
import { Icon } from '@iconify/vue'

onMounted(() => {
  const vts = new Vts('order', { halt: true })
  vts.form.addEventListener('submit', () => {
    Swal.fire({
      title: 'Na-add na sa cart',
      icon: 'success',
    })
  })
})
let qrCode
const show = ref(false)
function toQR() {
  show.value = true
  qrCode = new QRCodeStyling({
    width: 300,
    height: 300,
    type: 'svg',
    data: 'https://kaffeplus.vercel.app/',
    image: logo,
    dotsOptions: {
      color: '#4267b2',
      type: 'rounded',
    },
    backgroundOptions: {
      color: '#e9ebee',
    },
  })

  qrCode.append(document.getElementById('canvas'))
}

function toQRDL() {
  qrCode?.download({ name: 'qr', extension: 'svg' })
}

function toPDF() {
  const doc = new jsPDF()
  autoTable(doc, { html: '#order-table' })
  doc.text('Resibo idk', 15, 10)
  doc.save('order.pdf')
}
</script>

<style lang="scss" scoped>
.quantity-control {
  max-width: 150px;
}
</style>
