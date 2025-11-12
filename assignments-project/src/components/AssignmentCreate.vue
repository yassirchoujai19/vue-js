<template>
  <form @submit.prevent="submitForm" class="assignment-form">
    <input 
      v-model="newAssignment" 
      placeholder="✏️ Add a new assignment..." 
      :class="{ empty: !newAssignment }"
    />
    <button type="submit">Add</button>
  </form>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const newAssignment = ref('')
const emit = defineEmits(['add-assignment'])

function submitForm() {
  if (!newAssignment.value.trim()) return
  emit('add-assignment', newAssignment.value)
  newAssignment.value = ''
}

onMounted(() => {
  console.log('📥 AssignmentCreate mounted')
})
</script>

<style scoped>
.assignment-form {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 1.5rem;
  background: #f9fafb;
  border-radius: 12px;
  padding: 0.75rem 1rem;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
  transition: all 0.3s ease;
}

.assignment-form:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

.assignment-form input {
  flex: 1;
  padding: 0.6rem 0.9rem;
  border: 2px solid #e5e7eb;
  border-radius: 8px;
  font-size: 1rem;
  outline: none;
  transition: border-color 0.3s, box-shadow 0.3s;
}

.assignment-form input:focus {
  border-color: #3b82f6;
  box-shadow: 0 0 0 2px rgba(59, 130, 246, 0.2);
}

.assignment-form input.empty {
  border-color: #ef4444;
}

.assignment-form button {
  background: linear-gradient(90deg, #3b82f6, #2563eb);
  color: white;
  border: none;
  padding: 0.6rem 1.1rem;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 500;
  transition: background 0.3s, transform 0.2s;
}

.assignment-form button:hover {
  background: linear-gradient(90deg, #2563eb, #1d4ed8);
  transform: translateY(-1px);
}

.assignment-form button:active {
  transform: scale(0.98);
}
</style>
