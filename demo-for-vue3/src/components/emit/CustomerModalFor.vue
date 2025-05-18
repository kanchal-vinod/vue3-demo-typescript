<template>
    <teleport to="body">
      <div class="overlay">
        <div class="modal">
          <h2>Add New Person</h2>
  
          <div class="form-row">
            <input v-model="person.title" placeholder="Title" />
            <input v-model="person.firstName" placeholder="First Name *" />
            <input v-model="person.lastName" placeholder="Last Name *" />
          </div>
  
          <div class="form-row">
            <input v-model="person.email" placeholder="Email Address" />
            <input v-model="person.phone" placeholder="Phone Number" />
          </div>
  
          <div class="actions">
            <button @click="emit('save', person)">Save</button>
            <button @click="emit('close')">Cancel</button>
          </div>
        </div>
      </div>
    </teleport>
  </template>
  
  <script setup lang="ts">
  import { reactive } from 'vue'
  
  const emit = defineEmits(['save', 'close'])
  
  const person = reactive({
    title: 'Mr.',
    firstName: '',
    lastName: '',
    email: '',
    phone: '',
  })
  </script>
  
  <style scoped>
  .overlay {
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: rgba(0, 0, 0, 0.4);
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .modal {
    background: white;
    padding: 24px;
    border-radius: 8px;
    width: 600px;
  }
  
  .form-row {
    display: flex;
    gap: 12px;
    margin-bottom: 16px;
  }
  
  input {
    flex: 1;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .actions {
    text-align: right;
    display: flex;
    gap: 8px;
    justify-content: flex-end;
  }
  </style>
  

  <!-- <template>
  <div class="form-wrapper">
    <h1>Add New Rights Holder</h1>

    <div class="form-section">
      <label class="icon-label">
        <div class="icon-wrapper" @click="showModal = true">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="icon"
        viewBox="0 0 24 24"
        fill="currentColor"
      >
        <path
          d="M15 14c2.7 0 5 2.3 5 5v1H4v-1c0-2.7 2.3-5 5-5h6Zm-3-2a4 4 0 100-8 4 4 0 000 8Zm6-2V8h-2V6h2V4h2v2h2v2h-2v2h-2Z"
        />
      </svg>
    </div>

        Title
      </label>
      <input v-model="form.title" />
    </div>

    <div class="form-row">
      <input v-model="form.firstName" placeholder="First Name *" />
      <input v-model="form.lastName" placeholder="Last Name *" />
      <input v-model="form.email" placeholder="Email Address" />
    </div>

    <div class="form-row">
      <input v-model="form.phone" placeholder="Phone Number" />
      <input v-model="form.address" placeholder="Address" />
    </div>

    <div class="form-actions">
      <button @click="reset">Reset</button>
      <button @click="submit">Save</button>
    </div>

    <AddPersonModal
      v-if="showModal"
      @save="handleSave"
      @close="showModal = false"
    />
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'
import AddPersonModal from './components/emit/CustomerModalFor.vue'

const showModal = ref(false)

const form = reactive({
  title: '',
  firstName: '',
  lastName: '',
  email: '',
  phone: '',
  address: '',
})

function handleSave(person: any) {
  Object.assign(form, person)
  showModal.value = false
}

function reset() {
  Object.keys(form).forEach((key) => (form[key] = ''))
}

function submit() {
  alert(`✅ Saving form:\n${JSON.stringify(form, null, 2)}`)
}
</script>

<style scoped>
.form-wrapper {
  max-width: 1000px;
  margin: 40px auto;
  padding: 32px;
  border: 1px solid #ddd;
  border-radius: 12px;
  background: #fff;
}

.form-row {
  display: flex;
  gap: 12px;
  margin-bottom: 16px;
}

.form-section {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 16px;
}

input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 6px;
}

.icon-label img {
  width: 32px;
  height: 32px;
  cursor: pointer;
}

.form-actions {
  display: flex;
  justify-content: flex-end;
  gap: 12px;
  margin-top: 24px;
}
</style> -->
