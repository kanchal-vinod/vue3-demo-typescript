<script lang="ts" setup>
import { ref, computed } from 'vue'

const firstName = ref('')
const lastName = ref('')

// 👇 Auto-updated full name
const fullName = computed(() => `${firstName.value} ${lastName.value}`)
</script>

<template>
  <input v-model="firstName" placeholder="First name" />
  <input v-model="lastName" placeholder="Last name" />

  <p>Full Name: {{ fullName }}</p>
</template>
