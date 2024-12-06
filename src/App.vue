<script setup lang="ts">
import { ref } from "vue";
import type { Ref } from "vue";

interface Task {
  id: number;
  content: string;
  archived: boolean;
  important: boolean;
}

const newTask: Ref<string> = ref("Skibidi");

const tasks: Ref<Task[]> = ref([
  { id: 1, content: "aaa", archived: false, important: false },
  { id: 2, content: "bbb", archived: false, important: false }
]);

const addTask = (): void => {
  if (newTask.value !== "") {
    const id: number = Math.max(...tasks.value.map((element) => element.id), 0) + 1;

    tasks.value = [...tasks.value, { id: id, content: newTask.value, archived: false, important: false }];
    newTask.value = "";
  }
}

</script>

<template>
  <div class="screen">
    <div class="view">
      <button class="tasks">
        Tasks
      </button>
      <button class="Important">
        Important
      </button>
      <button class="archived">
        Archived
      </button>
    </div>

    <div class="new-task">
      <textarea v-model="newTask" placeholder="Enter your task here.">{{ newTask }}</textarea>
      <button @click=" addTask()">Submit</button>
    </div>

    <div class="tasks">
      <div class="task" v-for="task in tasks">
        <button class="complete">Complete</button>
        <div class="content">
          {{ task.content }}
        </div>

        <div class="side-functions">
          <button class="important">Important</button>
          <button class="delete">Delete</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">

</style>
