<template>
  <h1 class="my-6 ml-6 text-3xl text-zinc-700 font-bold">
    Welcome back, {{ user.name }}
  </h1>
  <div class="ml-4">
    <div class="mb-12">
      <form>
        <div class="flex ml-8 space-x-4">
          <input class="w-4" type="checkbox" name="" id="" />
          <input
            class="bg-transparent w-96 text-lg focus:outline-none focus:ring-0 focus:border-transparent border-zinc-700"
            placeholder="Add a new task"
            type="text"
          />
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
export default {
  data() {
    return {
      user: {
        name: "John Doe",
      },
    };
  },
};
</script>

<style>
body {
  background-color: #f5f5f5;
}
</style>
