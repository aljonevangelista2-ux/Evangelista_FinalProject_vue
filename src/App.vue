```vue
<script setup>
import { ref, computed } from 'vue'
import Header from './components/Header.vue'
import ProductList from './components/ProductList.vue'
import Cart from './components/Cart.vue'

const products = ref([
  {
    id: 1,
    name: 'T-Shirt',
    price: 350,
    emoji: '👕'
  },
  {
    id: 2,
    name: 'Sneakers',
    price: 1200,
    emoji: '👟'
  },
  {
    id: 3,
    name: 'Backpack',
    price: 850,
    emoji: '🎒'
  },
  {
    id: 4,
    name: 'Cap',
    price: 250,
    emoji: '🧢'
  },
  {
    id: 5,
    name: 'Watch',
    price: 1500,
    emoji: '⌚'
  },
  {
    id: 6,
    name: 'Headphones',
    price: 950,
    emoji: '🎧'
  }
])

const cart = ref([])

const addToCart = (product) => {
  const item = cart.value.find(
    item => item.id === product.id
  )

  if (item) {
    item.quantity++
  } else {
    cart.value.push({
      ...product,
      quantity: 1
    })
  }
}

const increaseQuantity = (item) => {
  item.quantity++
}

const decreaseQuantity = (item) => {
  if (item.quantity > 1) {
    item.quantity--
  } else {
    removeFromCart(item.id)
  }
}

const removeFromCart = (id) => {
  cart.value = cart.value.filter(
    item => item.id !== id
  )
}

const totalItems = computed(() => {
  return cart.value.reduce(
    (total, item) => total + item.quantity,
    0
  )
})

const cartTotal = computed(() => {
  return cart.value.reduce(
    (total, item) => {
      return total + item.price * item.quantity
    },
    0
  )
})

const checkout = () => {
  if (cart.value.length === 0) {
    alert('Your cart is empty!')
    return
  }

  alert(
    `Order placed successfully!\nTotal: ₱${cartTotal.value.toFixed(2)}`
  )

  cart.value = []
}
</script>

<template>
  <div class="app">

    <Header
      :total-items="totalItems"
    />

    <main>

      <ProductList
        :products="products"
        @add-to-cart="addToCart"
      />

      <Cart
        :cart="cart"
        :total-items="totalItems"
        :cart-total="cartTotal"
        @increase="increaseQuantity"
        @decrease="decreaseQuantity"
        @remove="removeFromCart"
        @checkout="checkout"
      />

    </main>

    <footer>
      <p>Mini Cart System © 2026</p>
    </footer>

  </div>
</template>
```