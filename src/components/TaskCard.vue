<template>
  <div class="flex bg-white rounded w-1/2 p-8 mb-2 shadow-lg justify-between">
    <div class="flex space-x-8">
      <input v-model="task.completed" type="checkbox" />
      <p :class="{ 'line-through': task.completed }">
        {{ task.title }}
      </p>
    </div>
    <button class="text-red-500" @click="$emit('remove-task')">Delete</button>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true,
    },
  },

  events: ["remove-task"],

  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped></style>
