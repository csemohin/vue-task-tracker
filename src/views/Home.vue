<template>
  <div class="home">
    <div class="container mt-5">
      <!-- task header start  -->
      <div class="d-flex justify-content-between">
        <navbar msg="Task Manager" />
        <Button type="btn-primary" text="Add Task" />
      </div>
      <!-- task header end -->
      <hr />
      <!-- add task start  -->
      <add-task />
      <!-- add task end -->
      <hr />
      <!-- task body start  -->
      <tasks
        @toggle-reminder="toggleReminder"
        @delete-task="deleteTask"
        :tasks="tasks"
      />
      <!-- task body end -->
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import Button from "@/components/Button.vue";
import Tasks from "@/components/Tasks.vue";
import AddTask from "@/components/AddTask.vue";

export default {
  name: "Home",
  components: {
    Navbar,
    Button,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((item) =>
        item.id == id ? { ...item, reminder: !item.reminder } : item
      );
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctor Appoinment",
        day: "March 1st at 2:30pm",
        reminder: false,
      },
      {
        id: 2,
        text: "Class Work",
        day: "March 2st at 2:30pm",
        reminder: false,
      },
      {
        id: 3,
        text: "Family Time",
        day: "December 5st at 2:30pm",
        reminder: true,
      },
    ];
  },
};
</script>
