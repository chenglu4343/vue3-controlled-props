<script setup lang="ts">
interface Task {
  title: string;
  done: boolean;
}

const props = defineProps<{
  task: Task;
}>();

const emits = defineEmits<{
  (e: 'update:task', newTask: Task): void;
}>();
</script>

<template>
  <div>
    <input v-model="task.done" type="checkbox" />
    <span>{{ task.title }}</span>
  </div>
</template>
