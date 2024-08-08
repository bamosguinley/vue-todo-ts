<script setup lang="ts">
import { ref } from "vue";

import TodoComponent from "@/components/TodoComponent.vue";
import type { Task } from "@types";
import TodoFormComponent from "@/components/TodoFormComponent.vue";

let tasks = ref<Task[]>([]);

let id = 0;
let getTask = (value: string) => {
  tasks.value.push({ id: id++, text: value, statut: false ,editable:false});
};



</script>

<template>
  <main>
    <TodoFormComponent @send_text="getTask" />
    <TodoComponent :tasks_data="tasks"/>
    <!-- {{ tasks }} -->
  </main>
</template>

<style scoped>
</style>
