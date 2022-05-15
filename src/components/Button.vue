<template>
  <button @click="handleClick" :style="{ background: color }" class="btn">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    color: {
      type: String,
      default: "black",
    },
    text: {
      type: String,
      required: true,
      default: "Add",
    },
  },
  methods: {
    handleClick() {
      this.$emit("btn-click");
    },
  },
};
</script>

