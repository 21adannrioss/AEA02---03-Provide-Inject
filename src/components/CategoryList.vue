<template>
  <div class="category-list">
    <h2>Productes</h2>
    <div class="products">
      <ProductItem v-for = "p in products" :key="p.name" :product="p"/>
    </div>
  </div>
</template>

<script setup>
  import { inject } from 'vue'
  import ProductItem from './ProductItem.vue'

  const products = inject('products')
</script>