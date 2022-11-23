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

    <div
      v-for="(task, index) in tasks"
      class="flex bg-white rounded w-1/2 p-8 mb-2 shadow-lg justify-between"
    >
      <div class="flex space-x-8">
        <input v-model="tasks[index].completed" type="checkbox" />
        <p :class="{ 'line-through': tasks[index].completed }">
          {{ task.title }}
        </p>
      </div>
      <button class="text-red-500">Delete</button>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const user = ref("John Doe");
    const task = ref({ title: "", completed: false });

    const tasks = ref([{ title: "Test", completed: false }]);

    const handleAddTask = () => {
      tasks.value.push(task.value);
      task.value = { title: "", completed: false };
    };

    return {
      handleAddTask,
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
