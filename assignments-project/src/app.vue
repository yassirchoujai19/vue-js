<template>
    <section class="app">
      <h1>📘 Assignments Tracker</h1>
  
      <assignment-create @add-assignment="addAssignment" />
  
      <div v-if="assignments.length">
        <assignment-list 
          :assignments="assignments" 
          @toggle-complete="toggleComplete"
        />
      </div>
  
      <p v-else>No assignments yet!</p>
    </section>
  </template>
  
  <script setup>
  import { ref, watch, onMounted, onUpdated } from 'vue'
  import AssignmentList from './components/AssignmentList.vue'
  import AssignmentCreate from './components/AssignmentCreate.vue'
  
  const assignments = ref([])
  
  onMounted(() => {
    console.log('✅ App mounted')
    assignments.value = [
      { id: 1, name: 'Math Homework', complete: false },
      { id: 2, name: 'Science Project', complete: true }
    ]
  })
  
  onUpdated(() => {
    console.log('🔁 App updated')
  })
  
  watch(assignments, (newVal) => {
    console.log('📊 Assignments changed:', newVal)
  }, { deep: true })
  
  function addAssignment(name) {
    assignments.value.push({
      id: Date.now(),
      name,
      complete: false
    })
  }
  
  function toggleComplete(id) {
    const assignment = assignments.value.find(a => a.id === id)
    assignment.complete = !assignment.complete
  }
  </script>
  
  <style scoped>
  .app {
    max-width: 600px;
    margin: auto;
    padding: 1rem;
    font-family: sans-serif;
  }
  </style>
  