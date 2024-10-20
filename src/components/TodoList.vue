<script setup>
import { defineProps, ref } from "vue";
import { useToast } from "vue-toastification";
const toast = useToast();
const props = defineProps({
  lists: {
    type: Array,
    required: true,
    default: () => [],
  },
});
const checkbox = ref(false);

const deleteTask = (index) => {
  props.lists.splice(index, 1);
  toast.success("Task deleted successfully!");
};

const handleCheckbox = () => {
  checkbox.value = !checkbox.value;

  toast.info("Task status updated!");
};
</script>

<template>
  <ul class="space-y-4">
    <li
      v-for="(task, index) in lists"
      :key="index"
      class="flex justify-between items-center bg-white shadow-md rounded-lg p-4">
      <span
        class="text-gray-800 font-medium"
        :class="checkbox == true ? 'line-through' : ''"
        >{{ task }}</span
      >
      <input type="checkbox" class="float-end" @click="handleCheckbox" />
      <button
        type="button"
        @click="deleteTask(index)"
        class="bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded-lg focus:outline-none focus:ring-2 focus:ring-red-400">
        Delete
      </button>
    </li>
  </ul>
</template>

<style scoped></style>
