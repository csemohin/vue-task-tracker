<template>
  <button type="button" :class="`btn ${type}`">{{ text }}</button>
</template>

<script>
export default {
  name: "button",
  props: {
    text: String,
    type: String,
  },
};
</script>

<style lang="scss" scoped></style>
