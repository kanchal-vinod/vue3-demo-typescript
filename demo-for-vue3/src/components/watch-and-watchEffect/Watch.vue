<template>
    <div class="wrapper">
      <h2>Search & Form Watcher</h2>
  
      <!-- Search Field -->
      <input v-model="search" placeholder="Search something..." />
  
      <!-- Form Fields -->
      <div class="form-section">
        <input v-model="form.firstName" placeholder="First Name" />
        <input v-model="form.email" placeholder="Email" />
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, reactive, watch, watchEffect } from 'vue'
  
  // 1. Search input value
  const search = ref('')
  
  // 2. Form object
  const form = reactive({
    firstName: '',
    email: '',
  })
  
  // ✅ WATCH — tracks specific value
  watch(search, (newVal, oldVal) => {
    console.log(`Search changed from "${oldVal}" to "${newVal}"`)
  })
  
  // ✅ WATCH EFFECT — tracks everything inside
  watchEffect(() => {
    console.log(`Form is now:`, {
      firstName: form.firstName,
      email: form.email
    })
  })
  </script>
  
  <style scoped>
  .wrapper {
    padding: 32px;
    max-width: 600px;
    margin: auto;
    background: #f9f9f9;
    border-radius: 8px;
  }
  
  input {
    display: block;
    width: 100%;
    margin-bottom: 12px;
    padding: 10px;
    font-size: 1rem;
  }
  </style>
  