```vue
<script setup>
import ProductCard from './ProductCard.vue'

defineProps({
  products: Array
})

defineEmits([
  'add-to-cart'
])
</script>

<template>
  <section class="products-section">

    <h2>Products</h2>

    <div class="products">

      <ProductCard
        v-for="product in products"
        :key="product.id"
        :product="product"
        @add-to-cart="$emit('add-to-cart', $event)"
      />

    </div>

  </section>
</template>
```