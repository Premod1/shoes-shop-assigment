<script setup>
import ProductDataNew from '@/stores/products.json'
import { computed, onMounted, ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const cartData = ref([])

// var totalPrice = ref()

const sizeChart = ref([
  { index: 1, value: '30' },
  { index: 2, value: '32' },
  { index: 3, value: '34' },
  { index: 4, value: '36' }
])

function viewCart() {
  const savedProductIds = JSON.parse(localStorage.getItem('clickedProductIds')) || []
  const productsInCart = savedProductIds
    .map((productId) => {
      const product = ProductDataNew.find((item) => item.id === productId)
      return product ? { ...product, quantity: 1 } : null
    })
    .filter(Boolean)

  cartData.value = productsInCart
  console.log(cartData.value)
}

function updateQTY(index) {
  cartData.value[index].quantity += 1
}

function removeQTY(index) {
  cartData.value[index].quantity -= 1
}

function purchaceNow() {
  localStorage.removeItem('clickedProductIds')
  cartData.value = {}
  router.push('/')
}

const totalPrice = computed(() => {
  let total = 0
  cartData.value.forEach((product) => {
    const priceWithoutCurrency = parseFloat(product.price.replace('$', ''))
    total += priceWithoutCurrency * product.quantity
  })
  return total.toFixed(2)
})

onMounted(() => {
  viewCart()
})
</script>
<template>
  <section class="text-gray-600 body-font">
    <div class="container px-5 py-24 mx-auto">
      <div class="flex flex-col text-center w-full mb-20">
        <h1 class="sm:text-4xl text-3xl font-medium title-font mb-2 text-gray-900">Cart</h1>
        <p class="lg:w-2/3 mx-auto leading-relaxed text-base">
          Banh mi cornhole echo park skateboard authentic crucifix neutra tilde lyft biodiesel
          artisan direct trade mumblecore 3 wolf moon twee
        </p>
      </div>
      <div class="lg:w-2/3 w-full mx-auto overflow-auto">
        <table class="table-auto w-full text-left whitespace-no-wrap">
          <thead>
            <tr>
              <th
                class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100 rounded-tl rounded-bl"
              >
                Image
              </th>
              <th
                class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100"
              >
                Price
              </th>
              <th
                class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100"
              >
                QTY
              </th>
              <th
                class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100"
              >
                SIZE
              </th>
              <th
                class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100"
              >
                Action
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(product, index) in cartData" :key="index">
              <td class="px-4 py-3">
                <a class="block relative h-48 w-80 rounded overflow-hidden">
                  <img
                    alt="ecommerce"
                    class="object-cover object-center w-full h-full block"
                    :src="product.imageSrc"
                  />
                </a>
              </td>
              <td class="px-4 py-3 text-lg text-gray-900">{{ product.price }}</td>
              <td class="px-4 py-3">{{ product.quantity }}</td>
              <td class="px-4 py-3">
                <select class="appearance-none border-none bg-gray-200 p-2 rounded-md">
                  <option value="" disabled selected>Select Size</option>
                  <option
                    v-for="sizeData in sizeChart"
                    :key="sizeData.index"
                    :value="sizeData.value"
                  >
                    {{ sizeData.value }}
                  </option>
                </select>
              </td>
              <td class="px-4 py-3 flex gap-5 px-30">
                <button
                  class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
                  @click="updateQTY(index)"
                >
                  + QTY
                </button>
                <button
                  class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded"
                  @click="removeQTY(index)"
                >
                  - QTY
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="flex pl-4 mt-4 lg:w-2/3 w-full mx-auto">
        <a class="text-indigo-500 text-3xl inline-flex items-center md:mb-2 lg:mb-0">
          <h2>Total: ${{ totalPrice }}</h2>
        </a>
        <button
          class="flex ml-auto text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-indigo-600 rounded"
          @click="purchaceNow"
        >
          Purchace Now
        </button>
      </div>
      <div></div>
    </div>
  </section>
</template>
