<template>
  <h1 class="my-6 ml-6 text-3xl text-zinc-700 font-bold">
    Welcome back, {{ user }}
  </h1>
  <div class="ml-4">
    <div class="mb-12">
      <form @submit.prevent="handleAddTask">
        <div class="flex ml-8 space-x-4">
          <input
            v-model="task.completed"
            class="w-4"
            type="checkbox"
            name=""
            id=""
          />
          <input
            v-model="task.title"
            class="bg-transparent w-96 text-lg focus:outline-none focus:ring-0 focus:border-transparent border-zinc-700"
            placeholder="Add a new task"
            type="text"
          />
        </div>
      </form>
    </div>

    <span v-if="!tasks.length" class="text-slate-400 ml-4"
      >There is no tasks saved</span
    >

    <h2 v-if="pendingTasks.length" class="my-4">Pending Tasks</h2>

    <TaskCard
      v-for="task in pendingTasks"
      :key="task.id"
      :task="task"
      @remove-task="handleRemoveTask(task.id)"
    />

    <h2 v-if="completedTasks.length" class="my-4">Completed Tasks</h2>
    <TaskCard
      v-for="task in completedTasks"
      :key="task.id"
      :task="task"
      @remove-task="handleRemoveTask(task.id)"
    />
  </div>
</template>

<script>
import { computed, ref } from "vue";
import TaskCard from "./components/TaskCard.vue";

import { v4 as uuidv4 } from "uuid";

export default {
  components: {
    TaskCard,
  },

  setup() {
    const user = ref("John Doe");
    const task = ref({ title: "", completed: false });

    const tasks = ref([{ id: uuidv4(), title: "Test", completed: false }]);

    const handleAddTask = () => {
      tasks.value.push({ ...task.value, id: uuidv4() });
      task.value = { title: "", completed: false };
    };

    const handleRemoveTask = (id) => {
      tasks.value = tasks.value.filter((task) => task.id !== id);
    };

    const completedTasks = computed(() =>
      tasks.value.filter((task) => task.completed)
    );
    const pendingTasks = computed(() =>
      tasks.value.filter((task) => !task.completed)
    );

    return {
      completedTasks,
      handleAddTask,
      handleRemoveTask,
      pendingTasks,
      task,
      tasks,
      user,
    };
  },
};
</script>

<style>
body {
  background-color: #f5f5f5;
}
</style>
