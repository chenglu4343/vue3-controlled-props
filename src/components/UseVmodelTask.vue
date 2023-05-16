<script setup lang="ts">
import { useVModel } from '@vueuse/core';

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

const task = useVModel(props, 'task', emits);
</script>

<template>
  <div>
    <input v-model="task.done" type="checkbox" />
    <span>{{ task.title }}</span>
  </div>
</template>
