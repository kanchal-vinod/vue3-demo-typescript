<template>
    <form @submit.prevent="handleSubmit">
      <!-- Name -->
      <div>
        <input
          v-model="form.name"
          @blur="touched.name = true"
          placeholder="Name"
        />
        <p v-if="!form.name && touched.name" class="error">Name is required</p>
      </div>
  
      <!-- Email -->
      <div>
        <input
          v-model="form.email"
          @blur="touched.email = true"
          placeholder="Email"
        />
        <p v-if="!isEmailValid && touched.email" class="error">Invalid email</p>
      </div>
  
      <!-- Password -->
      <div>
        <input
          v-model="form.password"
          @blur="touched.password = true"
          type="password"
          placeholder="Password"
        />
        <p v-if="!isPasswordValid && touched.password" class="error">
          Password must be at least 6 characters
        </p>
      </div>
  
      <!-- Confirm Password -->
      <div>
        <input
          v-model="form.confirmPassword"
          @blur="touched.confirmPassword = true"
          type="password"
          placeholder="Confirm Password"
        />
        <p
          v-if="!isConfirmPasswordValid && touched.confirmPassword"
          class="error"
        >
          Passwords do not match
        </p>
      </div>
  
      <!-- Submit Button -->
      <button type="submit" :disabled="!isFormValid">Submit</button>
    </form>
  </template>
  
  <script setup lang="ts">
  import { reactive, computed } from 'vue'
  
  const form = reactive({
    name: '',
    email: '',
    password: '',
    confirmPassword: ''
  })
  
  const touched = reactive({
    name: false,
    email: false,
    password: false,
    confirmPassword: false
  })
  
  // Individual validations
  const isEmailValid = computed(() =>
    /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)
  )
  
  const isPasswordValid = computed(() =>
    form.password.length >= 6
  )
  
  const isConfirmPasswordValid = computed(() =>
    form.password === form.confirmPassword && form.confirmPassword.length > 0
  )
  
  // Overall form status
  const isFormValid = computed(() =>
    form.name &&
    isEmailValid.value &&
    isPasswordValid.value &&
    isConfirmPasswordValid.value
  )
  
  function handleSubmit() {
    // mark everything as touched in case they skipped blur
    Object.keys(touched).forEach((key) => (touched[key as keyof typeof touched] = true))
  
    if (!isFormValid.value) return
  
    alert(`✅ Form submitted!\n\nName: ${form.name}\nEmail: ${form.email}`)
  }
  </script>
  
  <style scoped>
  .error {
    color: red;
    font-size: 0.85rem;
    margin-top: 4px;
  }
  </style>
  