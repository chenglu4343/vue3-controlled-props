<script setup lang="ts">
import { watch, ref } from 'vue';

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

const task = ref({ ...props.task });

/** 处理props值同步 */
watch(
  () => props.task,
  () => {
    task.value.done = props.task.done;
    task.value.title = props.task.title;
  },
  { deep: true }
);

/** 处理事件发送 */
watch(
  () => task,
  () => {
    emits('update:task', task.value);
  },
  { deep: true }
);
</script>

<template>
  <div>
    <input v-model="task.done" type="checkbox" />
    <span>{{ task.title }}</span>
  </div>
</template>
