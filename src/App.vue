<script setup>
import {ref} from 'vue';

if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
  document.documentElement.classList.add('dark')
} else {
  document.documentElement.classList.remove('dark')
}

const toggleDarkMode = ref(document.documentElement.className === 'dark');

const changeDarkMode = () => {
  toggleDarkMode.value = document.documentElement.classList.toggle("dark");
  toggleDarkMode.value
    ? (localStorage.theme = 'dark')
    : (localStorage.theme = 'light');
};
</script>

<template>
  <main class="container mx-auto text-center">
    <h1 class="text-center text-4xl dark:bg-gray-800 dark:text-white">
      Dark Mode
    </h1>
    <button
      class="bg-gray-700 text-white rounded-xl py-3 px-4"
      @click="changeDarkMode"
    >
      Dia/Noche {{ toggleDarkMode }}
    </button>
    
  </main>
  
  
</template>
