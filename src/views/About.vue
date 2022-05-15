<template>
  <h3>Version 1.0.0</h3>
  <p>This is the first app with vue</p>
  <router-link to="/">Go Back</router-link>
</template>

<script>
export default {
  name: "About",
  inheritAttrs: false, // disable 'non-props' warning
};
</script>