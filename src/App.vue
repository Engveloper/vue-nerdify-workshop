<template>
  <h1 class="my-6 ml-6 text-3xl text-zinc-700 font-bold">
    Welcome back, {{ user.name }}
  </h1>
  <div class="ml-4">
    <div class="mb-12">
      <form @submit.prevent="addTask">
        <div class="flex ml-8 space-x-4">
          <input v-model="completed" class="w-4" type="checkbox" />
          <input v-model="title"
            class="bg-transparent w-96 text-lg focus:outline-none focus:ring-0 focus:border-transparent border-zinc-700"
            placeholder="Add a new task" type="text" />
        </div>
      </form>
    </div>

    <div v-for="(task) in tasks" :key="task.id" class="flex space-x-8 bg-white rounded w-1/2 p-8 mb-4">
      <input v-model="task.completed" class="w-4" type="checkbox" />
      <p :class="{ 'line-through': task.completed }">{{ task.title }}</p>
    </div>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid"

export default {
  data() {
    return {
      completed: false,
      title: "",
      tasks: [],
      user: {
        name: "John Doe",
      },
    };
  },

  methods: {
    addTask() {
      const task = {
        id: uuidv4(),
        title: this.title,
        completed: this.completed
      }

      this.tasks.push(task);
    },
  },
};
</script>

<style>
body {
  background-color: #f5f5f5;
}
</style>
