<template>
  <header>
    <h1 title="我是待办清单 请输入您的Todo...">{{ title }}</h1>
    <TodoButton
      class="btn"
      @toggle-add-task="$emit('toggle-add-task')"
      :text="showAdd ? 'Close' : 'Add Todo'"
      :color="showAdd ? 'red' : 'black'"
      :title="showAdd ? '点我关闭' : '点我展开'"
    />
  </header>
</template>

<script>
import TodoButton from "./TodoButton.vue";

export default {
  components: { TodoButton },
  name: "TodoHeader",
  props: {
    title: String,
    showAdd: Boolean,
  },
  comments: {
    TodoButton,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
.btn {
  transition: 300ms;
}

.btn:hover {
  font-size: large;
}
</style>
