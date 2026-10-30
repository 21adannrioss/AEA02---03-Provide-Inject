<template>
  <div class="app-container">
    <h1>Botiga de Gadgets</h1>
    <div class="content">
      <!-- Els productes es passen per props al fill directe -->
      <CategoryList :products="products" />
      <!-- Cart rep el carret mitjançant inject -->
      <Cart />
    </div>
  </div>
</template>

<script setup>
import { reactive, provide } from 'vue'
import CategoryList from './components/CategoryList.vue'
import Cart from './components/Cart.vue'

// Carret reactiu compartit amb tots els descendents
const cart = reactive([])

const products = [
  {name: 'Auriculars Wireless 🎧', price: 50},
  {name: 'Smartwatch ⌚', price: 120},
  {name: 'Teclat Mecànic ⌨️', price: 80},
  {name: 'Altaveu Bluetooth 🔊', price: 60}
]

provide('cart', cart)
</script>

<style scoped>
.app-container {
  max-width: 900px;
  margin: 2rem auto;
  padding: 1rem;
  font-family: system-ui, sans-serif;
}
h1 {
  text-align: center;
  font-size: 1.6rem;
}
.content{
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 1.5rem;
  align-items: start;
}
@media (max-width: 640px){
  .content {
    grid-template-columns: 1fr;
  }
}
</style>