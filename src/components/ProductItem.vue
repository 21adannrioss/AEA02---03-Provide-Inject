<template>
  <div class="product-item">
    <div class="product-info">
      <span class="name">{{ product.name }}</span>
      <span class="price">{{ product.price }}€</span>
    </div>
    <button @click="addToCart">Add to cart</button>
  </div>
</template>

<script setup>
import { inject } from 'vue'

const props = defineProps(['product'])
const cart = inject('cart')

const addToCart = () => {
  if(!cart) {
    console.error("No s'ha proporcionat el carret mitjançant provide()")
    return
  }
  cart.push(props.product)
  alert(`${props.product.name} afegit al carret!`)
}
</script>

<style scoped>
.product-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.6rem 0.8rem;
  border: 1px solid #ddd;
  border-radius: 6px;
}
.product-info{
  display: flex;
  gap: 1rem;
  align-items: center;
}
.price {
  color: #555;
}
button {
  background: #42b883;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 0.35rem 0.8rem;
  cursor: pointer;
}
button:hover{
  background: #36a374;
}
</style>