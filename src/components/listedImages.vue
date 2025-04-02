<script setup>
import { ref } from 'vue';

const images = ref([
  'https://inspirothemes.com/polo/images/portfolio/64.jpg',
  'https://inspirothemes.com/polo/images/portfolio/60.jpg',
  'https://inspirothemes.com/polo/images/portfolio/61.jpg',
  'https://inspirothemes.com/polo/images/portfolio/65.jpg',
  'https://inspirothemes.com/polo/images/portfolio/68.jpg',
  'https://inspirothemes.com/polo/images/portfolio/69.jpg',
  'https://inspirothemes.com/polo/images/portfolio/69.jpg',
  'https://inspirothemes.com/polo/images/portfolio/69.jpg'

]);

const isModalOpen = ref(false);
const selectedImage = ref('');

const openModal = (image) => {
  selectedImage.value = image;
  isModalOpen.value = true;
};

const closeModal = () => {
  isModalOpen.value = false;
  selectedImage.value = '';
};
</script>

<template>

  <navBar />
  <aboutUs />


  <div class="container mx-auto p-4">
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
      <!-- Grid Item -->
      <div v-for="(image, index) in images" :key="index" class="relative group">
        <img :src="image" alt="Image" class="w-full h-auto rounded-lg" />

        <!-- Overlay (appears only on hover) -->
        <div class="absolute inset-0 bg-gray-400 bg-opacity-20 opacity-0 group-hover:opacity-50 transition duration-300 ease-in-out"></div>

        <!-- Circular Button -->
        <button
          class="absolute top-1/2 left-1/2 bg-white rounded-full p-3 shadow opacity-0 group-hover:opacity-100 transform scale-0 group-hover:scale-100 transition duration-300 ease-in-out -translate-x-1/2 -translate-y-1/2"
          @click="openModal(image)"
        >
          View
        </button>
      </div>
    </div>
  </div>

  <!-- Modal -->
  <div v-if="isModalOpen" class="fixed inset-0 flex items-center justify-center  bg-opacity-30 backdrop-blur-sm z-50">
    <div class="relative bg-white bg-opacity-90 p-4 rounded-lg shadow-lg max-w-3xl">
      <button @click="closeModal" class="absolute top-4 right-4 text-gray-600 hover:text-gray-900 text-5xl">&times;</button>
      <img :src="selectedImage" alt="Selected" class="max-w-full h-auto rounded-lg " />
    </div>
  </div>



</template>
