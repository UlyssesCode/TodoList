<template>
  <button @click="onClick()" class="btn" :style="{ background: color }">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "TodoButton",
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick() {
      this.$emit("toggle-add-task");
    },
  },
};
</script>

<style></style>
