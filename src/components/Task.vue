<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="['task p-3 mb-2', task.reminder ? 'reminder' : '']"
  >
    <div class="d-flex justify-content-between">
      <!-- left content start  -->
      <div class="information">
        <h3>{{ task.text }}</h3>
        <p>{{ task.day }}</p>
      </div>
      <!-- left content end -->
      <!-- right content end -->
      <div class="close-button">
        <button
          @click="$emit('delete-task', task.id)"
          type="button"
          class="btn btn-danger"
          aria-label="Close"
        >
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <!-- right content end -->
    </div>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
};
</script>

<style lang="scss" scoped>
.task {
  background-color: #f2f2f2;
  border: 1px solid #e7e7e7;
  &.reminder {
    border: 1px solid #777;
  }
}
</style>
