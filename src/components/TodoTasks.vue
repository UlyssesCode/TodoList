<template>
  <div>
    <h3 v-for="Task in Tasks" :key="Task.id">
      <TodoTask
        @toggle-reminder="$emit('toggle-reminder', Task.id)"
        @delete-Task="$emit('delete-Task', Task.id)"
        :Task="Task"
      />
    </h3>
  </div>
</template>

<script>
import TodoTask from "./TodoTask.vue";

export default {
  name: "TodoTasks",
  components: {
    TodoTask,
  },
  props: {
    Tasks: Array,
  },
  emits: ["delete-Task", "toggle-reminder"],
};
</script>

<style scoped></style>
