```vue
<script setup>
import { ref } from 'vue'
import QrcodeVue from 'qrcode.vue'
import CartItem from './CartItem.vue'

defineProps({
  cart: Array,
  totalItems: Number,
  cartTotal: Number
})

defineEmits([
  'increase',
  'decrease',
  'remove',
  'checkout'
])

const showQR = ref(false)

const showPaymentQR = () => {
  showQR.value = true
}
</script>

<template>
  <section class="cart-section">

    <h2>Shopping Cart</h2>

    <div
      v-if="cart.length === 0"
      class="empty-cart"
    >
      <div>🛒</div>
      <p>Your cart is empty.</p>
      <small>Add some products to your cart.</small>
    </div>

    <div v-else>

      <CartItem
        v-for="item in cart"
        :key="item.id"
        :item="item"
        @increase="$emit('increase', $event)"
        @decrease="$emit('decrease', $event)"
        @remove="$emit('remove', $event)"
      />

      <div class="cart-summary">

        <div>
          <span>Total Items:</span>
          <strong>{{ totalItems }}</strong>
        </div>

        <div class="total">
          <span>Total:</span>
          <strong>₱{{ cartTotal.toFixed(2) }}</strong>
        </div>

        <button
          class="checkout"
          @click="showPaymentQR"
        >
          Checkout
        </button>

      </div>

      <div
        v-if="showQR"
        class="qr-payment"
      >

        <h2>Payment QR Code</h2>

        <p>Scan this QR code to pay.</p>

        <div class="qr-box">
          <QrcodeVue
            value="Mini Cart System Payment"
            :size="220"
            level="H"
          />
        </div>

        <p class="payment-total">
          Amount: ₱{{ cartTotal.toFixed(2) }}
        </p>

        <button
          class="confirm-payment"
          @click="$emit('checkout')"
        >
          Confirm Payment
        </button>

      </div>

    </div>

  </section>
</template>
```