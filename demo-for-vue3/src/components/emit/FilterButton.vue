<template>
    <button @click="emit('selected', label)">
      {{ label }}
    </button>
  </template>
  
  <script lang="ts" setup>
  const emit = defineEmits<{
    (e: 'selected', label: string): void
  }>()
  
  defineProps<{
    label: string
  }>()
  </script>

<!-- use in parent following -->

<!-- <template>
    <h2>Selected: {{ selectedFilter }}</h2>
  
    <FilterButton label="All" @selected="handleSelect" />
    <FilterButton label="Active" @selected="handleSelect" />
    <FilterButton label="Completed" @selected="handleSelect" />
  </template>
  
  <script lang="ts" setup>
  import { ref } from 'vue'
  import FilterButton from './components/FilterButton.vue'
  
  const selectedFilter = ref('All')
  
  function handleSelect(label: string) {
    selectedFilter.value = label
  }
  </script> -->
  