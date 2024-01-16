<script setup>
import AboutImage from "../assets/about.jpg";
import FooterSmall from "@/components/FooterSmall.vue";
</script>
<template>
  <section class="text-gray-600 body-font">
  <div class="container mx-auto flex px-5 py-24 items-center justify-center flex-col">
    <img class="lg:w-2/6 md:w-3/6 w-5/6 mb-10 object-cover object-center rounded" alt="hero" :src="AboutImage">
    <div class="text-center lg:w-2/3 w-full">
      <h1 class="title-font sm:text-4xl text-3xl mb-4 font-medium text-gray-900">About Us</h1>
      <p class="mb-8 leading-relaxed">Meggings kinfolk echo park stumptown DIY, kale chips beard jianbing tousled. Chambray dreamcatcher trust fund, kitsch vice godard disrupt ramps hexagon mustache umami snackwave tilde chillwave ugh. Pour-over meditation PBR&B pickled ennui celiac mlkshk freegan photo booth af fingerstache pitchfork.</p>
      <div class="flex justify-center">
        
We have enabled the growth of our local industry with our endorsement of over 2000 small and medium local entrepreneurs, promoting private brands and labels through the supportive foundation of an established retail chain. And now, in keeping with our projected growth and expansion, Fashion Bug is exploring partnerships with multinational brands and retail houses to bring the Sri Lankan consumer direct and easy access to global trends, creating unrivaled fashion and lifestyle
      </div>
    </div>
  </div>
</section>
<FooterSmall/>
</template>
