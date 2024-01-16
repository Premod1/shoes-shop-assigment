<script setup>
import ProductData from '@/stores/products_cat.json';
import ProductDataNew from '@/stores/products.json';
import { ref, onMounted } from 'vue';

const productsCat = ref([])
const products = ref([])

onMounted(() => {
    productsCat.value = ProductData
    products.value = ProductDataNew
})
</script>
<template>
    <section class="text-gray-600 body-font">
  <div class="container px-5 py-24 mx-auto">
    <div class="flex justify-center">
        <h2 class="text-4xl leading-relaxed py-2">Product Categories</h2>
    </div>
    <hr/>
    <div class="flex flex-wrap -m-4">
      <div v-for="(product, index) in productsCat" :key="index" class="xl:w-1/4 md:w-1/2 p-4">
        <div class="bg-gray-100 p-6 rounded-lg">
          <img class="h-40 rounded w-full object-cover object-center mb-6" :src="product.imageSrc" alt="content">
          <h3 class="tracking-widest text-indigo-500 text-xs font-medium title-font">SUBTITLE</h3>
          <h2 class="text-lg text-gray-900 font-medium title-font mb-4">{{ product.title }}</h2>
          <p class="leading-relaxed text-base">Fingerstache flexitarian street art 8-bit waistcoat. Distillery hexagon disrupt edison bulbche.</p>
        </div>
      </div>
    </div>
  </div>
</section>
</template>