<template>
  <header
    class="bg-gray-800 text-white p-4 flex justify-between items-center relative"
  >
    <div class="flex items-center">
      <NuxtLink to="/">
        <img src="/images/logo.jpg" alt="لوگو" class="h-8" />
      </NuxtLink>
    </div>
    <div class="flex items-center">
      <button @click="toggleMenu" class="p-2 focus:outline-none">
        <svg
          v-if="!isMenuOpen"
          class="w-6 h-6"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 6h16M4 12h16m-7 6h7"
          ></path>
        </svg>
        <svg
          v-else
          class="w-6 h-6"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M6 18L18 6M6 6l12 12"
          ></path>
        </svg>
      </button>
    </div>
    <transition name="slide-fade">
      <div
        v-if="isMenuOpen"
        class="main-nav absolute right-0 bg-gray-800 text-white w-full h-screen lg:w-auto lg:h-auto"
      >
        <ul class="h-screen flex flex-col items-center">
          <li
            v-for="(item, index) in menuList"
            :key="index"
            class="p-4 border-b border-gray-700 w-full text-center"
          >
            <NuxtLink :to="item.url"> {{ item.title }} </NuxtLink>
          </li>
        </ul>
      </div>
    </transition>
  </header>
</template>

<script setup>
import { ref } from "vue";

const isMenuOpen = ref(false);

const menuList = [
  {
    title: "صفحه اصلی",
    url: "/",
  },
  {
    title: "جزئیات",
    url: "/about",
  },
];

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<style scoped>
.main-nav {
  top: 72px;
}
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.5s ease;
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(100%);
  opacity: 0;
}
.slide-fade-enter-to,
.slide-fade-leave-from {
  transform: translateX(0);
  opacity: 1;
}
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.5s ease;
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(100%);
  opacity: 0;
}
.slide-fade-enter-to,
.slide-fade-leave-from {
  transform: translateX(0);
  opacity: 1;
}
</style>
