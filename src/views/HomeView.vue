<script setup>
import ProductCategory from '@/components/ProductCategory.vue';
import ProductItem from '@/components/ProductItem.vue';
import FooterSmall from '@/components/FooterSmall.vue';
import HeaderSmall from '@/components/HeaderSmall.vue';

</script>

<template>
  <div>
    <HeaderSmall/>
    <ProductCategory />
    <ProductItem/>
    <hr />
    <FooterSmall />
  </div>
</template>
