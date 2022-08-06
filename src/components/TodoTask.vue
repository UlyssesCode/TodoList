<template>
  <div
    @dblclick="$emit('toggle-reminder', Task.id)"
    :class="[Task.reminder ? 'reminder' : '', 'Task']"
  >
    <h3 title="双击以切换状态">
      {{ Task.text }}
      <i
        title="坚持✊就是胜利"
        @click="$emit('delete-Task', Task.id)"
        class="fas fa-times"
      ></i>
    </h3>
    <p>{{ Task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "TodoTask",
  props: {
    Task: Object,
  },
};
</script>

<style scoped>
.fas {
  color: red;
  border-radius: 20%;
  transition: 200ms;
}
.fas:hover {
  color: black;
  font-size: 30px;
}

.Task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  transition: 200ms;
}
.Task:hover {
  background: rgb(188, 186, 186);
  font-size: larger;
}
.Task.reminder {
  border-left: 10px solid black;
}
.Task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
