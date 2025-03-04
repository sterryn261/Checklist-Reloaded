<script setup lang="ts">
import { ref } from "vue";
import type { Ref } from "vue";

import Tasks from "./components/Tasks.vue";

interface Task {
  id: number;
  content: string;
  archived: boolean;
  important: boolean;
}

export type { Task };

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
      <button class="important">
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

    <div class="list-of-tasks">
      <Tasks v-for="task in tasks" :task="task" />
    </div>
  </div>
</template>

<style scoped lang="scss">
.screen {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  align-content: center;
  gap: 1em;

  width: 100vw;
  height: 100vh;

  background: #aaa;

  .view {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;

    margin-top: 1em;
    width: 50%;

    button {
      position: relative;
      width: 25%;

      padding: 0.3em;

      font-size: 100%;
    }
  }

  .new-task {
    display: flex;
    flex-direction: row;
    justify-content: center;

    gap: 1em;

    textarea {
      width: 80%;
      font-size: 125%;
    }

    button {
      width: 5em;
      height: 5em;
    }
  }

  .list-of-tasks {
    display: flex;
    flex-direction: column;
    gap: 1em;
    width: 50vw;

    padding: 1em;

    background: #000;
  }
}
</style>
