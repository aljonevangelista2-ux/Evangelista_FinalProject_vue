```vue
<script setup>
defineProps({
  product: Object
})

defineEmits(['add-to-cart'])
</script>

<template>
  <div class="product-card">
    <div class="product-image">
      {{ product.emoji }}
    </div>

    <h3>{{ product.name }}</h3>

    <p class="price">
      ₱{{ product.price.toFixed(2) }}
    </p>

    <button @click="$emit('add-to-cart', product)">
      Add to Cart
    </button>
  </div>
</template>
```