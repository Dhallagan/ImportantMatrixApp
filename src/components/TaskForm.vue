<template>
  <div>
    <input v-model="task.Title" placeholder="Title" />
    <textarea v-model="task.Description" placeholder="Description"></textarea>

    <select v-model="task.ImportanceLevel">
      <option value="High Importance">High Importance</option>
      <option value="Low Importance">Low Importance</option>
    </select>

    <select v-model="task.UrgencyLevel">
      <option value="Urgent">Urgent</option>
      <option value="Not Urgent">Not Urgent</option>
    </select>

    <button @click="addTask">Add Task</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      task: {
        Title: "",
        Description: "",
        ImportanceLevel: "High Importance",
        UrgencyLevel: "Urgent",
      },
    };
  },
  methods: {
    addTask() {
      this.$emit("new-task", this.task);
      this.task = {
        Title: "",
        Description: "",
        ImportanceLevel: "Low Importance",
        UrgencyLevel: "Not Urgent",
      };
    },
  },
};
</script>
