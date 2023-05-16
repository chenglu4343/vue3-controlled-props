<script setup lang="ts">
import { toRefs } from 'vue';

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

const { task } = toRefs(props);
</script>

<template>
  <div>
    <input v-model="task.done" type="checkbox" />
    <span>{{ task.title }}</span>
  </div>
</template>
