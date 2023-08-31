<template>
  <div id="app">
    <TaskForm @new-task="addTask" />

    <div class="toggle-buttons">
      <button
        :class="{ active: currentView === 'matrix' }"
        @click="currentView = 'matrix'"
      >
        🔲 Matrix
      </button>
      <button
        :class="{ active: currentView === 'table' }"
        @click="currentView = 'table'"
      >
        📋 Table
      </button>
    </div>

    <MatrixDisplay v-if="currentView === 'matrix'" :tasks="tasks" />
    <TableDisplay v-if="currentView === 'table'" :tasks="tasks" />
  </div>
</template>

<script>
import TaskForm from "./components/TaskForm.vue";
import MatrixDisplay from "./components/MatrixDisplay.vue";
import TableDisplay from "./components/TableDisplay.vue";

export default {
  name: "App",
  components: {
    TaskForm,
    MatrixDisplay,
    TableDisplay,
  },
  data() {
    return {
      tasks: [],
      currentView: "matrix", // default view
    };
  },
  methods: {
    addTask(newTask) {
      this.tasks.push(newTask);
    },
  },
};
</script>

<style>
.toggle-buttons {
  display: flex;
  margin-top: 20px;
}

button {
  padding: 10px 15px;
  margin-right: 5px;
  cursor: pointer;
  border: none;
  background-color: #f2f2f2;
  transition: background-color 0.3s;
}

button.active {
  background-color: #007bff;
  color: white;
}

button:last-child {
  margin-right: 0;
}
</style>
