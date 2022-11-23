<template>
  <h1 class="my-6 ml-6 text-3xl text-zinc-700 font-bold">
    Welcome back, {{ user }}
  </h1>
  <div class="ml-4">
    <div class="mb-12">
      <form @submit.prevent="handleAddTask">
        <div class="flex ml-8 space-x-4">
          <input class="w-4" type="checkbox" name="" id="" />
          <input
            class="bg-transparent w-96 text-lg focus:outline-none focus:ring-0 focus:border-transparent border-zinc-700"
            placeholder="Add a new task"
            type="text"
          />
          <button type="button" @click="handleClick">Test</button>
        </div>
      </form>
    </div>

    <div class="flex space-x-8 bg-white rounded w-1/2 p-8">
      <input class="w-4" type="checkbox" />
      <p>Test</p>
    </div>
  </div>
</template>

<script>
import { ref, reactive, onMounted } from "vue";

export default {
  setup() {
    const user = ref("John Doe");
    const task = ref({ title: "", completed: false });

    onMounted(() => {
      console.log("mounted");
      setTimeout(() => {
        console.log("timeout");
        user.value = { name: "Jane Doe" };
      }, 2000);
    });

    const handleClick = () => {
      let test = user.value;
      console.log({ test });
      test = "Engels Doe";
      // user.value.name = "Engels Doe";
      console.log({ user });
    };

    return {
      handleClick,
      task,
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
