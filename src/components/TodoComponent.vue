<script setup lang="ts">
import { ref } from "vue";
const props = defineProps<{
  tasks_data: Array<Object>
}>()
let tasks = ref<(Object[])>([]);
tasks.value = props.tasks_data;


function removeTodo(todo: object): void {
  tasks.value = tasks.value.filter((t) => t !== todo);
}

let isFinish = ref<boolean>();
isFinish.value = false;
console.log(isFinish);

</script>

<template>
 <table class="table">
  <thead>
    <tr >
      <th scope="col">Tâche</th>
      <th scope="col">Statut</th>
      <th scope="col">Options</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="task in tasks" :key="task.id">
      <td><input class="form-check-input " type="checkbox" value="" id="flexCheckCheckedDisabled" v-model="isFinish" >{{task.text}}</td>
      <td>En cours</td>
      <td><button class="btn btn-primary">Update</button><button class="btn btn-danger" @click="removeTodo(task)">Delete</button></td>
    </tr>
  </tbody>
</table>
</template>

<style scoped>

</style>
