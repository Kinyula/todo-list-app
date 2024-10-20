<script setup>
import { ref } from "vue";
import { useToast } from "vue-toastification";
const task = ref("");
const tasks = ref([]);

const toast = useToast();
const emit = defineEmits(['task-created']);
const createTask = () => {
  if (task.value.trim() === "") {
    toast.error("Task cannot be empty");
    return;
  } else {
    tasks.value.push(task.value);
    task.value = "";
    toast.success("Task added successfully");

    // Emit the updated tasks data after adding a task
    const tasksData = {
      allTasks: tasks.value,
    };
    emit("task-created", tasksData);
  }
};
</script>

<template>
  <form
    @submit.prevent="createTask"
    method="post"
    class="p-6 flex items-center space-x-4 mt-6">
    <input
      type="text"
      v-model="task"
      class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
      placeholder="Enter a task..." />

    <button
      type="submit"
      class="bg-blue-600 text-white px-4 py-2 rounded-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500">
      Create
    </button>
  </form>
</template>

<style scoped></style>
