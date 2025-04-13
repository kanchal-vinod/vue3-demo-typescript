<template>
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
import UserForm from './components/emit/UserForm.vue'

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
</script>
