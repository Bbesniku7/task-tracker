<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      @btn-click="$emit('btn-click')"
      :color="showAddTask ? 'red' : 'green'"
      :text="showAddTask ? 'Close' : 'Add Task + '"
    />
  </header>
</template>

<script>
// Import components
import Button from "./Button.vue";

export default {
  name: "Header",
  components: {
    Button,
  },
  props: {
    title: {
      type: String,
      default: "Hello",
    },
    showAddTask: Boolean,
  },
  emits: ["btn-click"],
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>