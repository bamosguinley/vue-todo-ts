<script setup lang="ts">
import { ref, watch } from "vue";
import type { Task } from "@types";
const props = defineProps<{
  tasks_data: Array<Task>;
}>();


let tasks = ref<Task[]>([]);
tasks.value = props.tasks_data;

function removeTodo(todo: Task): void {
  tasks.value = tasks.value.filter((t) => t !== todo);
}


function setEditable(todo:Task): void{
  todo.editable = !todo.editable;
}
</script>

<template>
  <table class="table">
    <thead>
      <tr>
        <th scope="col">Tâche</th>
        <th scope="col">Statut</th>
        <th scope="col">Options</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="task in tasks" :key="task.id">
        <td>
          <input
            class="form-check-input mx-2"
            type="checkbox"
            v-model="task.statut"
          /><span :class="{ done: task.statut }" v-if="task.editable==false">{{ task.text }}</span>
          <input type="text" v-if="task.editable" v-model="task.text">
        </td>
        <td>{{ task.statut == false ? "En cours" : "Terminé" }}</td>
        <td>
          <button class="btn btn-primary"  v-if="task.statut==false" @click="setEditable(task)">{{task.editable==false?"Update":"Confirme"}}</button>
          <button class="btn btn-danger" @click="removeTodo(task)">
            Delete
          </button>
        </td>
      </tr>
    </tbody>
  </table>

</template>

<style scoped>
.done{
  text-decoration:line-through;
  color: red;
}
</style>
