<template>
  <table class="simple-table">
    <thead>
      <tr>
        <th>Name</th>
        <th>Age</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(row, index) in rows" :key="index">
        <td>{{ row.name }}</td>
        <td>{{ row.age }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script setup lang="ts">
interface Row {
  name: string
  age: number
}

defineProps<{
  rows: Row[]
}>()
</script>

<style scoped>
.simple-table {
  width: 100%;
  border-collapse: collapse;
}
.simple-table th,
.simple-table td {
  border: 1px solid #ccc;
  padding: 8px;
}
</style>
