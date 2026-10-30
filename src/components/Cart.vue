<template>
  <div class="cart">
    <h2>Carret</h2>

    <p v-if="cart.length === 0" class="empty">El carret està buit.</p>

    <template v-else>
      <p class="count">Tens {{ cart.length }} {{ cart.length === 1? 'article': 'articles' }} al carret</p>
      <ul>
        <CartItem v-for="(item, index) in cart" :key="index" :item="item" />
      </ul>
      <p class="total">Total: {{ total }}€</p>
      <button class="clear" @click="clearCart">🗑️ Buida carret</button>
    </template>
  </div>
</template>

<script setup>
import { inject, computed } from 'vue'
import CartItem from './CartItem.vue'

const cart = inject('cart')

const total = computed(() => cart.reduce((sum, p) => sum + p.price, 0))

const clearCart = () => {
  cart.splice(0, cart.length) // splice mantén la reactivitat del array
}
</script>

<style scoped>
.cart {
  border: 1px solid #ddd;
  border-radius: 6px;
  padding: 0.8rem 1rem;
}
ul {
  list-style: none;
  padding: 0;
  margin: 0.5rem 0;
}
.empty, .count {
  font-size: 0.85rem;
  color: #666;
}
.total {
  text-align: right;
  font-weight: bold;
}
.clear {
  width: 100%;
  background: #e5484d;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 0.4rem;
  cursor: pointer;
}
.clear:hover {
  background: #cc3a3f;
}
</style>