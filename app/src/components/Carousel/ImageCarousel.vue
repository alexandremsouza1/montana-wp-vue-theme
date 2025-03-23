<template>
  <div class="relative w-full my-8">
    <div class="bg-[#e5e5e5] rounded-lg p-16 flex flex-col items-center justify-center">
      <div class="mb-4">
        <div class="w-12 h-10 bg-white border border-[#ced4da] rounded flex items-center justify-center">
          <div class="w-6 h-4 bg-black"></div>
        </div>
      </div>
      <p class="text-[#000000] text-lg">License Management Dashboard</p>
    </div>
    
    <!-- Navigation arrows -->
    <button 
      class="absolute left-2 top-1/2 transform -translate-y-1/2 w-8 h-8 bg-white rounded-full flex items-center justify-center shadow-md"
      @click="prevSlide"
    >
      <span class="text-[#000000]">&lt;</span>
    </button>
    <button 
      class="absolute right-2 top-1/2 transform -translate-y-1/2 w-8 h-8 bg-white rounded-full flex items-center justify-center shadow-md"
      @click="nextSlide"
    >
      <span class="text-[#000000]">&gt;</span>
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const currentSlide = ref(0);
const slides = ref([
  { id: 1, title: 'License Management Dashboard' },
  { id: 2, title: 'Analytics Dashboard' },
  { id: 3, title: 'User Management' }
]);

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.value.length;
};

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + slides.value.length) % slides.value.length;
};
</script>

<style scoped>
/* Any component-specific styles can go here */
</style>