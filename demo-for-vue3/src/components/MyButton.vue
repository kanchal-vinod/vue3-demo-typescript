<template>
    <button @click="handleClick">{{ label }}</button>
  </template>
  
  <script lang="ts" setup>
  defineProps<{
    label: string
  }>()
  
  function handleClick() {
    alert('Button clicked!')
  }
  </script>
  