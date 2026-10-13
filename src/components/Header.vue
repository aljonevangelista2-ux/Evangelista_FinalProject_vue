```vue
<script setup>
defineProps({
  totalItems: Number
})
</script>

<template>
  <header>
    <div>
      <h1>🛒 Mini Cart</h1>
      <p>Simple Vue Shopping System</p>
    </div>

    <div class="cart-count">
      🛒 {{ totalItems }}
    </div>
  </header>
</template>
```