<template>
    <form @submit.prevent="handleSubmit">
      <input v-model="name" type="text" placeholder="Your name" />
      <input v-model="email" type="email" placeholder="Your email" />
      <button type="submit">Submit</button>
    </form>
  </template>
  
  <script lang="ts" setup>
  import { ref } from 'vue'
  
  // Define emit and what it sends: an object with name and email
  const emit = defineEmits<{
    (e: 'submitForm', formData: { name: string; email: string }): void
  }>()
  
  const name = ref('')
  const email = ref('')
  
  function handleSubmit() {
    emit('submitForm', {
      name: name.value,
      email: email.value,
    })
  }
  </script>
  

<!-- use following on parent -->

  <!-- <template>
    <h2>User Form</h2>
    <UserForm @submitForm="handleFormSubmit" />
  
    <div v-if="submitted">
      <h3>Submitted Data:</h3>
      <p>Name: {{ form.name }}</p>
      <p>Email: {{ form.email }}</p>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { ref } from 'vue'
  import UserForm from './components/UserForm.vue'
  
  const submitted = ref(false)
  const form = ref({
    name: '',
    email: ''
  })
  
  // This runs when the child emits 'submitForm'
  function handleFormSubmit(data: { name: string; email: string }) {
    form.value = data
    submitted.value = true
  }
  </script> -->
  