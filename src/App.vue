<template>
  <div class="app-container">
    <h2>Botiga de Gadgets</h2>
    <div class="content">
      <CategoryList/>
      <Cart/>
    </div>
  </div>
</template>

<script setup>
  import { reactive, provide } from 'vue'
  import CategoryList from './components/CategoryList.vue'
  import Cart from './components/Cart.vue'

  const cart = reactive({})
  const products = [
    { name: "Auriculars Wireless 🎧", price: 50 },
    { name: "Smartwatch ⌚", price: 120 },
    { name: "Teclat Mecànic ⌨️", price: 80 },
    { name: "Altaveu Bluetooth 🔊", price: 60 }
  ]

  provide('cart', cart)
  provide('products', products)
</script>



<style scoped>
  .app-container {
    max-width: 900px;
    margin: 2rem auto;
    padding: 1rem;
  }

</style>