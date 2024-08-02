
<script setup lang="ts">
import { ref } from "vue";

const emit= defineEmits(["send_text"]);
const task_text = ref("");

const send = (): void => {
  emit("send_text", task_text.value);
  task_text.value = "";
};
</script>

<template>
  <form class="row g-3" @submit.prevent="send()">
    <div class="col-auto">
      <input
        type="text"
        class="form-control"
        placeholder="votre tâche..."
        v-model="task_text"
      />
    </div>
    <div class="col-auto">
      <input type="submit" class="btn btn-primary mb-3" value="Add task" />
    </div>
  </form>
</template>

<style scoped>
</style>
