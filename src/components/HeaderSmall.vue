<script setup>
import { useRouter } from 'vue-router';

const router = useRouter();

function contact() {
  router.push('/contact');
}
</script>
<template>
    <div class="bg-cover bg-center  h-auto text-white lg:py-48 py-24 px-12 object-fill" style="background-image: url(https://images.unsplash.com/photo-1558981806-ec527fa84c39?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80)">
       <div class="md:w-1/2">
        <p class="font-bold text-sm uppercase">Services</p>
        <p class="text-3xl font-bold">Multimedia products</p>
        <p class="text-2xl mb-10 leading-none">Atractive designs for your brand</p>
        <a href="#" class="bg-purple-800 py-4 px-8 text-white font-bold uppercase text-xs rounded hover:bg-gray-200 hover:text-gray-800" @click="contact">Contact us</a>
        </div>  
    </div>
</template>