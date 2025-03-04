<script setup lang="ts">
import type { Task } from '../App.vue';

const props = defineProps<{
  task: Task,
  view: string
}>();

const filter = (): boolean => {
  if ((props.view === "tasks" && props.task.archived === false) ||
    (props.view === "important" && props.task.archived === false && props.task.important === true) ||
    (props.view === "archived" && props.task.archived === true)) {
    return true;
  }
  return false;
}


</script>

<template>
  <div v-if="filter()" class="task">
    <button class="completed" @click="$emit('completed')">Complete</button>
    <div class="content">
      {{ props.task.content }}
    </div>

    <div class="side-functions">
      <button class="important" @click="$emit('important')">Important</button>
      <button class="archive" @click="$emit('archived')">Archive</button>
    </div>
  </div>
</template>

<style scoped lang="scss">
.task {
  display: flex;
  flex-direction: row;

  position: relative;
  padding: 1em;

  background: #fff;


  .content {
    word-wrap: break-word;
    width: 70%;

    margin-left: 1em;
  }

  .side-functions {
    position: absolute;
    right: 0;

    button {
      margin-right: 1em;
    }
  }
}
</style>