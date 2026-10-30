<template>
  <li class="cart-item">
    <span>{{ item.name }}</span>
    <span>- {{ item.price }}€</span>
  </li>
</template>

<script setup>
defineProps({
  item: {
    type: Object,
    required: true
  }
})
</script>

<style scoped>
.cart-item {
  display: flex;
  gap: 0.4rem;
  padding: 0.2rem 0;
  font-size: 0.9rem;
}
</style>