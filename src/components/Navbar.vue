<template>
  <h2 class="navbar-area">{{ msg }}</h2>
</template>

<script>
export default {
  name: "navbar",
  props: {
    msg: String,
  },
};
</script>

<style lang="scss" scoped></style>
