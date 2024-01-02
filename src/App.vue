<script setup lang="ts">
import { ref, watch } from 'vue';
import SimpleTask from './components/SimpleTask.vue';
import ToRefTask from './components/ToRefTask.vue';
import UseVmodelTask from './components/UseVmodelTask.vue';
import ControlledTask from './components/ControlledTask.vue';
import UnControlledTask from './components/UnControlledTask.vue';
import DefineModel from './components/DefineModel.vue';

const lists = ref(
  Array.from({ length: 6 }).map((item, index) => ({
    title: `title${index}`,
    done: false,
  }))
);

const isControlledCheck = ref(false);
const isUnControlledCheck = ref(false);

function handleUpdateControlledTask(task) {
  if (isControlledCheck.value) {
    lists.value[3] = task;
  }
}

function handleUpdateUnControlledTask(task) {
  if (isUnControlledCheck.value) {
    lists.value[4] = task;
  }
}
</script>

<template>
  <!-- change directly -->
  <div class="task">
    <span>SimpleTask</span>
    <SimpleTask :task="lists[0]" />
    {{ lists[0] }}
  </div>

  <!-- change directly -->
  <div class="task">
    <span>ToRefTask</span>
    <ToRefTask :task="lists[1]" />
    {{ lists[1] }}
  </div>

  <!-- change directly -->
  <div class="task">
    <span>UseVmodelTask</span>
    <UseVmodelTask :task="lists[2]" />
    {{ lists[2] }}
  </div>

  <!-- change defineModel -->
  <div class="task">
    <span>defineModelTask</span>
    <DefineModel :task="lists[3]"/>
    {{ lists[3] }}
  </div>


  <!-- change controlled -->
  <div class="mt-20">
    isAcceptChanged
    <input type="checkbox" v-model="isControlledCheck" />
  </div>
  <div class="task">
    <span>ControlledTask</span>
    <ControlledTask
      :task="lists[4]"
      @update:task="handleUpdateControlledTask"
    />
    {{ lists[4] }}
  </div>

  <!-- change unControlled -->
  <div class="mt-20">
    isAcceptChanged
    <input type="checkbox" v-model="isUnControlledCheck" />
  </div>
  <div class="task">
    <span>UnControlledCheck</span>
    <UnControlledTask
      :task="lists[5]"
      @update:task="handleUpdateUnControlledTask"
    />
    {{ lists[5] }}
  </div>
</template>

<style>
.task {
  display: flex;
  align-items: center;
  gap: 10px;
}

.mt-20 {
  margin-top: 20px;
}
</style>
