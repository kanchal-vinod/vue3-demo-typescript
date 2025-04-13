<template>
    <button @click="clicked">{{ label }}</button>
  </template>
  
  <script lang="ts" setup>
  defineProps<{
    label: string
  }>()

  const emit =defineEmits(['clicked'])
  
  function handleClick() {
    alert('Button clicked!')
  }
  </script>
  