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

<style scoped lang="scss"></style>