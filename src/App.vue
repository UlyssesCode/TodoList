<template>
  <div class="container">
    <TodoHeader
      @toggle-add-task="toggleAddTask"
      title="Todo List"
      :showAdd="showAdd"
    />
    <div v-show="showAdd">
      <AddTask @add-task="addTask" />
    </div>
    <TodoTasks
      @toggle-reminder="toggleReminder"
      @delete-Task="deleteTask"
      :Tasks="Tasks"
    />
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoTasks from "./components/TodoTasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: {
    TodoHeader,
    TodoTasks,
    AddTask,
  },
  data() {
    return {
      Tasks: JSON.parse(localStorage.getItem("Tasks")) || [
        { id: 100, text: "Study JavaScript", day: "2022.1.1", reminder: true },
        { id: 200, text: "Eat", day: "2022.1.1", reminder: true },
        { id: 300, text: "Sleep", day: "2022.1.1", reminder: false },
      ],
      showAdd: true,
    };
  },
  methods: {
    toggleAddTask() {
      this.showAdd = !this.showAdd;
    },
    addTask(task) {
      this.Tasks.push(task);
    },
    deleteTask(id) {
      if (confirm("确定吗?"))
        this.Tasks = this.Tasks.filter((Task) => Task.id != id);
    },
    toggleReminder(id) {
      this.Tasks.map((Task) =>
        Task.id === id ? (Task.reminder = !Task.reminder) : ""
      );
    },
  },
  watch: {
    Tasks(value) {
      localStorage.setItem("Tasks", JSON.stringify(value));
    },
  },
  // created() {
  //   this.Tasks = [
  //     { id: 100, text: "Study", day: "2022.1.1", reminder: true },
  //     { id: 200, text: "Eat", day: "2022.1.1", reminder: true },
  //     { id: 300, text: "Sleep", day: "2022.1.1", reminder: false },
  //   ];
  // },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
