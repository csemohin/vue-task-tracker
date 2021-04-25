<template>
  <div class="home">
    <div class="d-flex justify-content-between">
      <navbar msg="Task Manager" />
      <Button type="btn-primary" text="Add Task" />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import Button from "@/components/Button.vue";

export default {
  name: "Home",
  components: {
    Navbar,
    Button,
  },
};
</script>
