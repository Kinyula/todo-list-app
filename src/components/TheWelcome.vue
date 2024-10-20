<script setup>
import { ref } from "vue";

const isMenuOpen = ref(false);
</script>

<template>
  <header class="bg-gray-800">
    <nav
      class="container mx-auto p-4 flex justify-between items-center relative">
      <div class="text-white text-2xl font-bold">
        <router-link to="/">MyApp</router-link>
      </div>

      <div class="md:hidden">
        <button
          class="text-white focus:outline-none"
          @click="isMenuOpen = !isMenuOpen">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="2"
            stroke="currentColor"
            class="w-6 h-6">
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M4 6h16M4 12h16m-7 6h7" />
          </svg>
        </button>
      </div>

      <ul class="hidden md:flex space-x-6 text-white">
        <li>
          <router-link to="/" class="hover:text-gray-400">Home</router-link>
        </li>
        <li>
          <router-link to="/about" class="hover:text-gray-400"
            >About</router-link
          >
        </li>
      </ul>

      <ul
        :class="isMenuOpen ? 'absolute left-0 top-full w-full block' : 'hidden'"
        class="md:hidden bg-gray-800 space-y-2 text-white">
        <li>
          <router-link to="/" class="block py-2 px-4 hover:bg-gray-700"
            >Home</router-link
          >
        </li>
        <li>
          <router-link to="/about" class="block py-2 px-4 hover:bg-gray-700"
            >About</router-link
          >
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>
nav {
  z-index: 10;
}
</style>
