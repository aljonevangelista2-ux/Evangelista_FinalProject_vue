```vue
<script setup>
import { ref } from 'vue'

const name = ref('')
const email = ref('')
const phone = ref('')
const address = ref('')
const city = ref('')
const province = ref('')
const zip = ref('')
const delivery = ref('Standard Delivery')
const payment = ref('GCash')
</script>

<template>
  <section class="personal-details">
    <div class="section-title">
      <div class="title-icon">👤</div>
      <div>
        <h2>Personal Details</h2>
        <p>Enter your information for delivery</p>
      </div>
    </div>

    <div class="form-grid">

      <div class="form-group">
        <label>Full Name</label>
        <input
          v-model="name"
          type="text"
          placeholder="Juan Dela Cruz"
        />
      </div>

      <div class="form-group">
        <label>Email Address</label>
        <input
          v-model="email"
          type="email"
          placeholder="juan@email.com"
        />
      </div>

      <div class="form-group">
        <label>Phone Number</label>
        <input
          v-model="phone"
          type="tel"
          placeholder="09XX XXX XXXX"
        />
      </div>

      <div class="form-group">
        <label>ZIP Code</label>
        <input
          v-model="zip"
          type="text"
          placeholder="6340"
        />
      </div>

      <div class="form-group full">
        <label>Complete Address</label>
        <textarea
          v-model="address"
          placeholder="House number, street, barangay"
        ></textarea>
      </div>

      <div class="form-group">
        <label>City / Municipality</label>
        <input
          v-model="city"
          type="text"
          placeholder="Enter city or municipality"
        />
      </div>

      <div class="form-group">
        <label>Province</label>
        <input
          v-model="province"
          type="text"
          placeholder="Enter province"
        />
      </div>

      <div class="form-group">
        <label>Delivery Method</label>
        <select v-model="delivery">
          <option>Standard Delivery</option>
          <option>Express Delivery</option>
          <option>Pickup</option>
        </select>
      </div>

      <div class="form-group">
        <label>Payment Method</label>
        <select v-model="payment">
          <option>GCash</option>
          <option>Cash on Delivery</option>
          <option>Bank Transfer</option>
        </select>
      </div>

    </div>
  </section>
</template>
```