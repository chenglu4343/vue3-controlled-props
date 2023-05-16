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

function handleChange(e: any) {
  emits('update:task', {
    ...props.task,
    done: e.target.checked,
  });

  e.target.checked = props.task.done;
}
</script>

<template>
  <div>
    <input :checked="task.done" type="checkbox" @change="handleChange" />
    <span>{{ task.title }}</span>
  </div>
</template>
