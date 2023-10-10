<template>
  <div>
    <main>
      <!-- Header -->
      <header>
        <img src="./assets/pinia-logo.svg" alt="Pinia Logo" />
        <h1>Tihana Task</h1>
      </header>

      <!-- New Task -->
      <div class="new-task-form">
        <TaskForm />
      </div>

      <!-- Filter -->
      <nav class="filter">
        <button @click="filter = 'all'">All tasks</button>
        <button @click="filter = 'favs'">Fav tasks</button>
      </nav>

      <!-- Task Lists -->
      <div v-if="filter === 'all'" class="task-list">
        <p>You have {{ taskStore.totalCount }} tasks left to do.</p>
        <div v-for="task in taskStore.tasks">
          <TaskDetails :task="task" />
        </div>
      </div>

      <div v-if="filter === 'favs'" class="task-list">
        <p>You have {{ taskStore.favCount }} fav left to do.</p>
        <div v-for="task in taskStore.favs">
          <TaskDetails :task="task" />
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import { ref } from 'vue'
import TaskDetails from './components/TaskDetails.vue'
import TaskForm from './components/TaskForm.vue'
import { useTaskStore } from './stores/TaskStore'

export default {
  components: { TaskDetails, TaskForm },

  setup() {
    const taskStore = useTaskStore()

    const filter = ref('all')

    return { taskStore, filter }
  }
}
</script>
