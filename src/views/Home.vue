<template>
  <div class="home">
    <div class="container mt-5">
      <!-- task header start  -->
      <div class="d-flex justify-content-between">
        <navbar msg="Task Manager" />
        <Button
          @toggle-button-task="toggleButton"
          :type="showAddTask ? 'btn-danger' : 'btn-primary'"
          :text="showAddTask ? 'Close Task' : 'Add Task'"
        />
      </div>
      <!-- task header end -->
      <hr />
      <!-- add task start  -->
      <div v-show="showAddTask">
        <add-task @add-task="addTask" />
      </div>
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
      showAddTask: false,
    };
  },
  methods: {
    toggleButton() {
      this.showAddTask = !this.showAddTask;
    },
    async addTask(task) {
      const res = await fetch("http://localhost:5000/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(task),
      });
      const data = res.json();
      this.tasks = [...this.tasks, data];
    },
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
    async fetchTasks() {
      const res = await fetch("http://localhost:5000/tasks");
      const data = res.json();
      return data;
    },
    async fetchTask(id) {
      const res = await fetch(`http://localhost:5000/tasks/${id}`);
      const data = res.json();
      return data;
    },
  },
  async created() {
    this.tasks = await this.fetchTasks();
  },
};
</script>
