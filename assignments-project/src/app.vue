<script setup>
import { ref, onMounted } from 'vue'
import AssignmentList from './components/AssignmentList.vue'
import AssignmentCreate from './components/AssignmentCreate.vue'

const assignments = ref([])

onMounted(() => {
  assignments.value = [
    { id: 1, name: 'Math Homework', complete: false },
    { id: 2, name: 'Science Project', complete: true }
  ]
})

function addAssignment(name) {
  assignments.value.push({
    id: Date.now(),
    name,
    complete: false
  })
}

function toggleComplete(id) {
  const assignment = assignments.value.find(a => a.id === id)
  if (assignment) assignment.complete = !assignment.complete
}

function deleteAssignment(id) {
  assignments.value = assignments.value.filter(a => a.id !== id)
}
</script>

<template>
  <section class="app">
    <h1>📘 Assignments Tracker</h1>

    <assignment-create @add-assignment="addAssignment" />

    <div v-if="assignments.length">
      <assignment-list 
        :assignments="assignments"
        @toggle-complete="toggleComplete"
        @delete-assignment="deleteAssignment"
      />
    </div>

    <p v-else>No assignments yet!</p>
  </section>
</template>

  
  <style scoped>
  .app {
    max-width: 600px;
    margin: auto;
    padding: 1rem;
    font-family: sans-serif;
  }
  </style>
  