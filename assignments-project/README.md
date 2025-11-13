🧾 Assignments Tracker

  A simple and elegant Vue 3 project built with Vite — designed to help you manage and track assignments.
  This project demonstrates the core concepts of Vue such as ref, reactive, v-if, v-for, v-on, v-bind, v-model, emit, watch, and lifecycle hooks         (onMounted, onUpdated).

  🚀 Features
  
  ✏️ Add new assignments
  
  ✅ Mark assignments as complete / undo
  
  ❌ Delete assignments
  
  👀 Dynamic list rendering using v-for
  
  🧠 Reactive state management with ref
  
  🔗 Two-way binding using v-model
  
  🔔 Event communication via emit
  
  ⏱️ Lifecycle hooks for mounted and updated states
  
  👁️ Watcher to track reactive data changes
  
  💅 Modern responsive design with smooth hover effects

🧰 Tech Stack

  Vue 3 (Composition API)

  Vite (for fast development and build)
  
  Bun (for package management and scripts)
  
  HTML + CSS + JavaScript (ES Modules)

🧑‍💻 Recommended Setup

  IDE:
  
  VS Code
  
  Vue (Official Extension)
   (disable Vetur)

  Browser Tools:
  
  Vue.js Devtools for Chrome
  
  Vue.js Devtools for Firefox

⚙️ Project Setup
  bun install

🧩 Compile and Hot-Reload for Development
  bun dev

🏗️ Compile and Minify for Production
  bun run build

📂 Project Structure
src/
├── components/
│   ├── AssignmentCreate.vue   # Input form to add new assignments
│   ├── AssignmentList.vue     # Displays and manages the list
├── App.vue                    # Main app with logic & watcher
├── main.js                    # Entry point

🧠 What You’ll Learn

Difference between Composition API and Options API

How to use reactivity with ref and watch

How to handle parent-child communication with emit

Using lifecycle hooks (onMounted, onUpdated)

Clean component-based UI structure
