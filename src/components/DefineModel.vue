<script setup lang="ts">
interface Task {
  title: string
  done: boolean
}

const task = defineModel<Task>('task', {
  type: Object,
  required: true,
})
</script>

<template>
  <div>
    <input v-model="task.done" type="checkbox" />
    <span>{{ task.title }}</span>
  </div>
</template>
