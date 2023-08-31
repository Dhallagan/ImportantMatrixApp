<template>
  <div class="table-wrapper">
    <table>
      <thead>
        <tr>
          <th>Title</th>
          <th>Description</th>
          <th>Importance</th>
          <th>Urgency</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="task in orderedTasks" :key="task.Title">
          <td>{{ task.Title }}</td>
          <td>{{ task.Description }}</td>
          <td>{{ task.ImportanceLevel }}</td>
          <td>{{ task.UrgencyLevel }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    tasks: Array,
  },
  computed: {
    orderedTasks() {
      const order = ["High Importance", "Low Importance"];
      return this.tasks.sort((a, b) => {
        return (
          order.indexOf(a.ImportanceLevel) - order.indexOf(b.ImportanceLevel) ||
          order.indexOf(a.UrgencyLevel) - order.indexOf(b.UrgencyLevel)
        );
      });
    },
  },
};
</script>

<style scoped>
.table-wrapper {
  max-width: 800px;
  margin: 20px auto;
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th,
td {
  padding: 8px 12px;
  border: 1px solid #ccc;
}

th {
  background-color: #f7f7f7;
}
</style>
