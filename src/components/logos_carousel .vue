<script setup>
import { ref, computed } from 'vue';

const currentIndex = ref(0);
const itemsPerView = ref(5);
const logos = ref([
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: '../src/assets/google.png', alt: 'Envato' },
  { src: 'https://via.placeholder.com/150?text=Apple', alt: 'Apple' }
]);

const totalPages = computed(() => Math.ceil(logos.value.length / itemsPerView.value));
</script>
<style>
button:focus {
  outline: none;
}
</style>


<template>
  <div class="flex flex-col items-center w-full p-4">
      <div class="overflow-hidden w-full max-w-4xl">
        <div
          class="flex gap-4 transition-transform duration-500 ease-in-out"
          :style="{ transform: `translateX(-${currentIndex * (100 / totalPages)}%)` }"
        >
          <div v-for="(logo, index) in logos" :key="index" class="w-1/5 flex-shrink-0 flex justify-center">
            <img :src="logo.src" :alt="logo.alt" class="h-16 md:h-24 object-contain" />
          </div>
        </div>
      </div>
      <div class="flex space-x-2 mt-4">
        <button
          v-for="(_, index) in totalPages"
          :key="index"
          @click="currentIndex = index"
          class="h-3 w-3 rounded-full"
          :class="currentIndex === index ? 'bg-gray-800' : 'bg-gray-400'"
        ></button>
      </div>
    </div>
</template>
