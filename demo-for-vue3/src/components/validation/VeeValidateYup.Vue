<template>
    <Form :validation-schema="schema" @submit="onSubmit">
      <!-- Name -->
      <Field name="name" placeholder="Name" />
      <ErrorMessage name="name" class="error" />
  
      <!-- Email -->
      <Field name="email" placeholder="Email" />
      <ErrorMessage name="email" class="error" />
  
      <button type="submit">Submit</button>
    </Form>
  </template>
  
  <script setup lang="ts">
  import { Form, Field, ErrorMessage } from 'vee-validate'
  import * as yup from 'yup'
  
  // 🧠 Define your validation rules
  const schema = yup.object({
    name: yup.string().required('Name is required'),
    email: yup.string().required('Email is required').email('Invalid email'),
  })
  
  function onSubmit(values: any) {
    alert(`✅ Form submitted!\n${JSON.stringify(values, null, 2)}`)
  }
  </script>
  
  <style scoped>
  .error {
    color: red;
    font-size: 0.9rem;
    margin-bottom: 10px;
    display: block;
  }
  </style>
  