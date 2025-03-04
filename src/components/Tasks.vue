<script setup lang="ts">
import type { Task } from '../App.vue';

const props = defineProps<{
  task: Task
}>();

</script>

<template>
  <div class="task">
    <button class="complete">Complete</button>
    <div class="content">
      {{ props.task.content }}
    </div>

    <div class="side-functions">
      <button class="important">Important</button>
      <button class="delete">Delete</button>
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
    color: #ffffff;
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