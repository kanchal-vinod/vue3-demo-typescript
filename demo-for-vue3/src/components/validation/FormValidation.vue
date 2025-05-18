<template>
    <form @submit.prevent="submit">
      <input v-model="form.name" placeholder="Name" />
      <p v-if="errors.name" class="error">{{ errors.name }}</p>
  
      <input v-model="form.email" placeholder="Email" />
      <p v-if="errors.email" class="error">{{ errors.email }}</p>
  
      <button type="submit">Submit</button>
    </form>
  </template>
  
  <script setup lang="ts">
  import { reactive } from 'vue'
  
  const form = reactive({
    name: '',
    email: '',
  })
  
  const errors = reactive({
    name: '',
    email: '',
  })
  
  function submit() {
    // Reset errors
    errors.name = ''
    errors.email = ''
  
    // Validate name
    if (!form.name) {
      errors.name = 'Name is required'
    }
  
    // Validate email
    if (!form.email) {
      errors.email = 'Email is required'
    } else if (!form.email.includes('@')) {
      errors.email = 'Invalid email format'
    }
  
    // If no errors, show success
    if (!errors.name && !errors.email) {
      alert(`✅ Submitted:\n${JSON.stringify(form, null, 2)}`)
    }
  }
  </script>
  
  <style scoped>
  .error {
    color: red;
    font-size: 0.9rem;
    margin-bottom: 10px;
  }
  </style>
  