
<template>
    <div class="product-item">
        <div class="product-info">
            <span class="name">{{ product.name }}</span>
            <span class="price">{{ product.price }}</span>
        </div>

        <button @click="addToCart">Add to cart</button>
    </div>
</template>

<script setup>
import { inject } from 'vue';

const props = defineProps(['product']);
const cart = inject('cart');

const addToCart = () => {
    if (!cart) {
        console.error('No se ha proporcionado el carrito mediante provide()');
        return;
    }

    cart.push(props.product);
    alert(`${props.product.name} añadido al carrito!`);
};
</script>

<style scoped>
</style>