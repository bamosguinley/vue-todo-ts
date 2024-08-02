<script setup lang="ts">
import { ref } from "vue";

import TodoComponent from "@/components/TodoComponent.vue";

import TodoFormComponent from "@/components/TodoFormComponent.vue";

interface Task {
  id: number;
  text: string;
  statut: string;
}

let tasks = ref<Task[]>([]);


let id = 0;
let getTask = (t: string):void => {
  tasks.value.push({ id: id++, text: t, statut: "en attente" });
};



</script>

<template>
  <main>
    <TodoFormComponent @send_text="getTask" />
    <TodoComponent :tasks_data="tasks"/>
    {{ tasks }}
  </main>
</template>

<style scoped>
</style>
