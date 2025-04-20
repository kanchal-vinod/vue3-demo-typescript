<template>
    <div>
      <h2>Edit Names</h2>
      <div v-for="(person, index) in people" :key="index">
        <input v-model="person.name" />
        <button @click="remove(index)">Remove</button>
      </div>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { reactive } from 'vue'
  
  const people = reactive([
    { name: 'Kanchal' },
    { name: 'Sasha' },
    { name: 'Nimal' }
  ])
  
  function remove(index: number) {
    people.splice(index, 1)
  }
  </script>
  