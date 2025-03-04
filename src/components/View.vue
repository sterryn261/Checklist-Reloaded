<script setup lang="ts">

const emit = defineEmits(['update'])
const update = (e: string): void => {
  emit('update', e)
}

</script>

<template>
  <div class="view">
    <button class="tasks" @click="() => { update('tasks') }">
      Tasks
    </button>
    <button class="important" @click="() => { update('important') }">
      Important
    </button>
    <button class="archived" @click="() => { update('archived') }">
      Archived
    </button>
  </div>
</template>

<style scoped lang="scss">
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
</style>