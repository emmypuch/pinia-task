<template>
  <div>
    <main>
      <header>
        <img src="./assets/pinia-logo.svg" alt="Pinia Logo" />
        <h1>Tihana Task</h1>
      </header>
    </main>
  </div>
</template>

<script>
import { useTaskStore } from './stores/TaskStore'

export default {
  setup() {
    const taskStore = useTaskStore()

    return { taskStore }
  }
}
</script>
