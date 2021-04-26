<template>
  <button @click="onClick()" type="button" :class="`btn ${type}`">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "button",
  props: {
    text: String,
    type: String,
  },
  methods: {
    onClick() {
      this.$emit("toggle-button-task");
    },
  },
};
</script>

<style lang="scss" scoped></style>
