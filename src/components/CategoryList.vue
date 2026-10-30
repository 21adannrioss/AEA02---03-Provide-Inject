<template>
  <div class="category-list">
    <h2>Productes</h2>
    <div class="products">
      <ProductItem v-for="p in products" :key="p.name" :product="p" />
    </div>
  </div>
</template>

<script setup>
import ProductItem from './ProductItem.vue'

// Els productes arriben del component pare per props
defineProps({
  products: {
    type: Array,
    required: true
  }
})
</script>

<style scoped>
.products {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}
</style>