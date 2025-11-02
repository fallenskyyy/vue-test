<script setup lang="ts">
import {ref} from 'vue';

const status = ref(true);
const tasks = ref(["Task one", "Task two", "Task three"]);
const newTask = ref("")

const link = ref("https://google.com")
const toggleStatus = () =>{
  status.value = !status.value;
}

const addTask = () =>{
  if(newTask.value.trim() !== ""){
    tasks.value.push(newTask.value)
    newTask.value = ""
  }
}

const deleteTask = (index: number) =>{
  tasks.value.splice(index, 1)
}
</script>

<template>
  <h1>Vue test</h1>
  <p v-if="status">
    status is true
  </p>
  <p v-else>
    status is false
  </p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add new task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">Create</button>
  </form>

  <ul>
      <li v-for="(task, index) in tasks" :key="task">{{task}}
        <button @click="deleteTask(index)">X</button>
      </li>
  </ul>

  <a :href="link">Google</a>
  <br>
  <button @click="toggleStatus">Change status</button>
</template>

<style scoped></style>
