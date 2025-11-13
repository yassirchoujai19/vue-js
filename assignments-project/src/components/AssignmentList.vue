<template>
  <div class="assignments">
    <h2>📚 Assignments <span>({{ assignments.length }})</span></h2>

    <ul>
      <li 
        v-for="assignment in assignments" 
        :key="assignment.id"
        :class="{ complete: assignment.complete }"
      >
        <div class="content">
          <span class="title">{{ assignment.name }}</span>
          <span class="status" :class="{ done: assignment.complete }">
            {{ assignment.complete ? '✓ Completed' : '⏳ Pending' }}
          </span>
        </div>

        <div class="buttons">
          <button 
            @click="$emit('toggle-complete', assignment.id)"
            :class="assignment.complete ? 'undo' : 'complete-btn'"
          >
            {{ assignment.complete ? 'Undo' : 'Mark Complete' }}
          </button>

          <button 
            @click="$emit('delete-assignment', assignment.id)"
            class="delete-btn"
          >
            Delete
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup>
const props = defineProps({
  assignments: {
    type: Array,
    required: true
  }
})
</script>

<style scoped>
.assignments {
  background: #f9fafb;
  padding: 1.5rem;
  border-radius: 16px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  transition: box-shadow 0.3s ease;
}

.assignments:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

.assignments h2 {
  margin-bottom: 1rem;
  font-weight: 600;
  color: #111827;
  display: flex;
  align-items: center;
  gap: 8px;
}

.assignments h2 span {
  color: #6b7280;
  font-size: 0.9rem;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: white;
  border-radius: 10px;
  padding: 0.9rem 1rem;
  margin-bottom: 0.75rem;
  transition: background 0.3s, transform 0.2s, box-shadow 0.3s;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
}

li:hover {
  background: #f3f4f6;
  transform: translateY(-2px);
}

.complete {
  opacity: 0.8;
  background: #ecfdf5;
}

.content {
  display: flex;
  flex-direction: column;
}

.title {
  font-weight: 500;
  color: #1f2937;
}

.status {
  font-size: 0.85rem;
  color: #6b7280;
}

.status.done {
  color: #16a34a;
  font-weight: 500;
}

.buttons {
  display: flex;
  gap: 0.5rem;
}

button {
  border: none;
  border-radius: 8px;
  padding: 0.5rem 1rem;
  font-size: 0.9rem;
  cursor: pointer;
  font-weight: 500;
  transition: all 0.25s ease;
}

button.complete-btn {
  background: linear-gradient(90deg, #10b981, #059669);
  color: white;
}

button.complete-btn:hover {
  background: linear-gradient(90deg, #059669, #047857);
  transform: translateY(-1px);
}

button.undo {
  background: linear-gradient(90deg, #f59e0b, #d97706);
  color: white;
}

button.undo:hover {
  background: linear-gradient(90deg, #d97706, #b45309);
  transform: translateY(-1px);
}

button.delete-btn {
  background: linear-gradient(90deg, #f87171, #dc2626);
  color: white;
}

button.delete-btn:hover {
  background: linear-gradient(90deg, #dc2626, #b91c1c);
  transform: translateY(-1px);
}
</style>
