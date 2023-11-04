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

    <button type="button" class="btn btn-primary mt-3 me-3" @click="toPDF">
      gawa pdf resibo idk
    </button>
    <button type="button" class="btn btn-primary mt-3">gawa qr code</button>

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
import Swal from 'sweetalert2'
import Vts from 'vts.js'
import { onMounted } from 'vue'
import jsPDF from 'jspdf'
import autoTable from 'jspdf-autotable'

onMounted(() => {
  const vts = new Vts('order', { halt: true })
  vts.form.addEventListener('submit', () => {
    Swal.fire({
      title: 'Na-add na sa cart',
      icon: 'success',
    })
  })
})

function toPDF() {
  const doc = new jsPDF()
  autoTable(doc, { html: '#order-table' })
  doc.text('Resibo idk', 15, 10)
  doc.save('order.pdf')
}
</script>

<style lang="scss" scoped></style>
