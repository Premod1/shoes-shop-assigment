<script setup>
import ProductData from '@/stores/products_cat.json';
import ProductDataNew from '@/stores/products.json';
import { ref, onMounted } from 'vue';

const productsCat = ref([])
const products = ref([])

let clickedProductIds = JSON.parse(localStorage.getItem('clickedProductIds')) || [];

const handleItemClick = (productsId) => {
  clickedProductIds.push(productsId);
  localStorage.setItem('clickedProductIds', JSON.stringify(clickedProductIds));
  alert('Add to Cart');
}


onMounted(() => {
    productsCat.value = ProductData
    products.value = ProductDataNew
})
</script>
<template>
     <section class="text-gray-600 body-font">
        <div class="container px-5 py-24 mx-auto">
            <div class="flex justify-center">
                <h2 class="text-4xl leading-relaxed py-2">Products</h2>
             </div>
         <hr/>
          <div class="flex flex-wrap -m-4">
            <div v-for="(pro, i) in products" :key="i" class="lg:w-1/4 md:w-1/2 p-4 w-full"  @click="handleItemClick(pro.id)">
              <a class="block relative h-48 rounded overflow-hidden">
                <img
                  alt="ecommerce"
                  class="object-cover object-center w-full h-full block"
                  :src="pro.imageSrc"
                />
              </a>
              <div class="mt-4">
                <h3 class="text-gray-500 text-xs tracking-widest title-font mb-1">{{ pro.category }}</h3>
                <h2 class="text-gray-900 title-font text-lg font-medium">{{ pro.title }}</h2>
                <p class="mt-1">{{ pro.price }}</p>
                <button class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded">
                    Add to Cart
                </button>
              </div>
            </div>
          </div>
        </div>
      </section>
</template>