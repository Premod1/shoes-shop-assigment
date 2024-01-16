<script setup>
import FooterSmall from '@/components/FooterSmall.vue';
import ProductData from '@/stores/products_cat.json';
import ProductDataNew from '@/stores/products.json';
import { ref, onMounted } from 'vue';

const productsCat = ref([])
const products = ref([])
let filteredProducts = ref([]);

let clickedProductIds = JSON.parse(localStorage.getItem('clickedProductIds')) || [];

const handleItemClick = (productsId) => {
  clickedProductIds.push(productsId);
  localStorage.setItem('clickedProductIds', JSON.stringify(clickedProductIds));
  alert('Add to Cart');
}

const searching = () => {
  const searchInput = document.getElementById('default-search').value.toLowerCase();
  filteredProducts.value = products.value.filter(product => product.title.toLowerCase().includes(searchInput));
  console.log(filteredProducts.value);
}

onMounted(() => {
    productsCat.value = ProductData
    products.value = ProductDataNew
    filteredProducts.value = products.value;
})
</script>
<template>
  <div class="flex">
    <div class="flex-none w-1/4 hidden md:block">
      <section class="text-gray-600 body-font">
        <div class="container px-5 py-36 mx-auto">
            <div class="flex justify-center">
                <h2 class="text-4xl leading-relaxed py-2">Categories</h2>
             </div>
          <div v-for="(product, index) in productsCat" :key="index" class="lg-1/4 md:w-1/2 p-4 w-full">
            <a class="block relative h-48 w-80 rounded overflow-hidden">
              <img
                alt="ecommerce"
                class="object-cover object-center w-full h-full block"
                :src="product.imageSrc"
              />
            </a>
            <div class="mt-4">
              <h3 class="text-gray-500 text-xs tracking-widest title-font mb-1">{{ product.category }}</h3>
              <h2 class="text-gray-900 title-font text-lg font-medium">{{ product.title }}</h2>
            </div>
          </div>

        </div>
      </section>
    </div>
    <div class="flex-grow lg:w-3/4">
      <section class="text-gray-600 body-font">
        <div class="container px-5 py-24 mx-auto">
            <div>
              <div>
  <label for="default-search" class="mb-2 text-sm font-medium text-gray-900 sr-only dark:text-white">Search</label>
  <div class="relative">
    <div class="absolute inset-y-0 start-0 flex items-center ps-3 pointer-events-none">
      <svg class="w-4 h-4 text-gray-500 dark:text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 20 20">
        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"/>
      </svg>
    </div>
    <input type="search" id="default-search" class="block w-full p-4 ps-10 text-sm text-black border border-gray-300 rounded-lg bg-white focus:ring-blue-500 focus:border-blue-500 dark:bg-white dark:border-gray-600 dark:placeholder-gray-400 dark:text-black dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Searching Items......" required>
    <button @click="searching" type="submit" class="text-white absolute end-2.5 bottom-2.5 bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-4 py-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Search</button>
  </div>
</div>

            </div>
            <div class="flex justify-center">
                <h2 class="text-4xl leading-relaxed py-2">Products</h2>
             </div>
          <div  class="flex flex-wrap -m-4">
            <div v-for="(pro, i) in filteredProducts" :key="i" class="lg:w-1/4 md:w-1/2 p-4 w-full" @click="handleItemClick(pro.id)">
              <a class="block relative h-48 rounded overflow-hidden">
                <img
                  alt="ecommerce"
                  class="object-cover object-center w-full h-full block"
                  :src="pro.imageSrc"
                />
              </a>
              <div class="mt-4">
                <h3 class="text-gray-500 text-xs tracking-widest title-font mb-1">CATEGORY</h3>
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
    </div>
  </div>
  <hr/>
  <FooterSmall/>
</template>
