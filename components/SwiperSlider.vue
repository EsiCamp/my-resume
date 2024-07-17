<template>
  <swiper
    :modules="modules"
    :slides-per-view="1"
    navigation
    :pagination="{ clickable: true }"
    class="my-4 mySwiper"
  >
    <swiper-slide v-for="(slide, index) in slides" :key="index">
      <img :src="slide.src" :alt="slide.alt" class="w-full h-auto" />
    </swiper-slide>
  </swiper>
</template>

<script setup>
import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Pagination } from "swiper/modules";

import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";

const modules = [Navigation, Pagination];

// Define your slides data
const slides = ref([
  {
    src: "/images/logo.jpg",
    alt: "logo",
  },
  {
    src: "/images/test.jpg",
    alt: "test",
  },
]);
</script>

<style scoped>
.mySwiper {
  width: 100%;
  height: 100%;
}
img {
  display: block;
  width: 100%;
  height: auto;
  aspect-ratio: 16/9;
}
</style>
