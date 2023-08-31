<template>
  <div class="matrix">
    <div
      v-for="importance in ['Low Importance', 'High Importance']"
      :key="importance"
    >
      <div v-for="urgency in ['Not Urgent', 'Urgent']" :key="urgency">
        <div>{{ importance }} - {{ urgency }}</div>
        <ul>
          <li
            v-for="task in filterTasks(importance, urgency)"
            :key="task.Title"
          >
            {{ task.Title }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tasks: Array,
  },
  methods: {
    filterTasks(importance, urgency) {
      return this.tasks.filter(
        (task) =>
          task.ImportanceLevel === importance && task.UrgencyLevel === urgency
      );
    },
  },
};
</script>

<style scoped>
.matrix {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  max-width: 800px;
  margin: 20px auto;
  border: 1px solid #ccc;
  padding: 20px;
}

.matrix > div {
  display: grid;
  grid-template-rows: repeat(2, 1fr);
  gap: 10px;
}

.matrix > div > div {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 8px;
}

.matrix > div > div > div:first-child {
  font-weight: bold;
  margin-bottom: 10px;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}
</style>
