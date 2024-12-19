<template>
    <div class="relative w-full max-w-7xl mx-auto h-96 overflow-hidden rounded-lg shadow-lg">
      <div v-for="(image, index) in images" :key="index" 
           class="absolute top-0 left-0 w-full h-full transition-opacity duration-1000 ease-in-out"
           :class="{ 'opacity-100': index === currentIndex, 'opacity-0': index !== currentIndex }">
        <img :src="image.src" :alt="image.alt" class="w-full h-full object-cover">
      </div>
      
      <button @click="prevSlide" 
              class="absolute top-1/2 left-4 transform -translate-y-1/2 bg-black bg-opacity-50 text-white p-2 rounded-full hover:bg-opacity-75 transition-all"
              aria-label="Previous slide">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
        </svg>
      </button>
      
      <button @click="nextSlide"
              class="absolute top-1/2 right-4 transform -translate-y-1/2 bg-black bg-opacity-50 text-white p-2 rounded-full hover:bg-opacity-75 transition-all"
              aria-label="Next slide">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
        </svg>
      </button>
      
      <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-2">
        <button v-for="(_, index) in images" :key="index"
                @click="setCurrentIndex(index)"
                :class="{ 'bg-white': index === currentIndex, 'bg-white bg-opacity-50': index !== currentIndex }"
                class="w-3 h-3 rounded-full"
                :aria-label="`Go to slide ${index + 1}`">
        </button>
      </div>
    </div>
  </template>
  
  <script>

  export default {
    data() {
      return {
        currentIndex: 0,
        images: window.vueVars.carouselImages.map((src, index) => ({
          src: src,
          alt: `Slide ${index + 1}`
        }))
      }
    },
    methods: {
      nextSlide() {
        this.currentIndex = (this.currentIndex + 1) % this.images.length
      },
      prevSlide() {
        this.currentIndex = (this.currentIndex - 1 + this.images.length) % this.images.length
      },
      setCurrentIndex(index) {
        this.currentIndex = index
      }
    },
    mounted() {
      setInterval(this.nextSlide, 5000) // Auto-advance every 5 seconds
    }
  }
  </script>
  
  <style scoped>
  /* Adicione estilos específicos aqui, se necessário */
  </style>