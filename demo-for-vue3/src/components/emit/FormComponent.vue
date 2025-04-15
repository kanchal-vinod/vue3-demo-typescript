<template>
  <form @submit.prevent="onSubmit">
    <input v-model="form.name" placeholder="Name" />
    <input v-model="form.email" placeholder="Email" />
    <input v-model="form.age" type="number" placeholder="Age" />
    <input v-model="form.country" placeholder="Country" />
    <textarea v-model="form.message" placeholder="Message"></textarea>
    <button type="submit">Submit</button>
  </form>
</template>

<script setup lang="ts">
import { reactive } from 'vue'

/** 1. Define the emit type */
const emit = defineEmits<{
  (e: 'form-submitted', payload: FormData): void
}>()

/** 2. Define form data interface */
interface FormData {
  name: string
  email: string
  age: number | null
  country: string
  message: string
}

/** 3. Create reactive form object */
const form = reactive<FormData>({
  name: '',
  email: '',
  age: null,
  country: '',
  message: ''
})

/** 4. Emit data on submit */
function onSubmit() {
  emit('form-submitted', { ...form })
}
</script>


<!-- <template>
    <FormComponent @form-submitted="handleForm" />
  </template>
  
  <script setup lang="ts">
  import FormComponent from './components/emit/FormComponent.vue'
  
  function handleForm(data: {
    name: string
    email: string
    age: number | null
    country: string
    message: string
  }) {
    console.log('Received form data from child:', data)
  }
  </script> -->
  