<script setup lang="ts">
import { useForm, useField } from 'vee-validate'
import { required, email, min } from '@vee-validate/rules'
import { defineRule } from 'vee-validate'

// 1️⃣ Define rules
defineRule('required', required)
defineRule('email', email)
defineRule('min', min)

// 2️⃣ Setup form
const { handleSubmit } = useForm()

// 3️⃣ Create fields with rules
const { value: name, errorMessage: nameError } = useField('name', 'required')
const { value: emailField, errorMessage: emailError } = useField('email', 'required|email')
const { value: password, errorMessage: passwordError } = useField('password', 'required|min:6')

// 4️⃣ Handle submit
function onSubmit(values: any) {
  alert(`✅ Submitted!\nName: ${values.name}\nEmail: ${values.email}`)
}
</script>

<template>
  <form @submit="handleSubmit(onSubmit)">
    <!-- Name -->
    <div>
      <input v-model="name" placeholder="Name" />
      <span class="error">{{ nameError }}</span>
    </div>

    <!-- Email -->
    <div>
      <input v-model="emailField" placeholder="Email" />
      <span class="error">{{ emailError }}</span>
    </div>

    <!-- Password -->
    <div>
      <input v-model="password" type="password" placeholder="Password" />
      <span class="error">{{ passwordError }}</span>
    </div>

    <button type="submit">Submit</button>
  </form>
</template>

<style scoped>
.error {
  color: red;
  font-size: 0.85rem;
  margin-top: 4px;
  display: block;
}
</style>
