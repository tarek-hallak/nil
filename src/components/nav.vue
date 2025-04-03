<script setup>
import { onMounted, ref } from 'vue';

const isScrolled = ref(false);
const isMenuOpen = ref(false);

const updateScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

onMounted(() => {
  window.addEventListener('scroll', updateScroll);
});
</script>

<template>
  <section>
    <div class="overflow-hidden bg-[url('hero.jpg')] bg-cover bg-center h-screen w-full">
      <!-- Navbar -->
      <div :class="['fixed top-0 left-0 w-full z-50 transition-all duration-300', isScrolled ? 'bg-black text-white' : 'bg-transparent text-black']">
        <div class="flex justify-between items-center px-6 py-4">
          <!-- Logo -->
          <img :src="isScrolled ? '../src/assets/white-logo.png' : '../src/assets/black-logo.png'" alt="Logo" class="h-10">

          <div class="flex gap-4 items-center">
            <!-- Menu Items -->
            <ul :class="['md:flex space-x-6 items-center text-lg font-bold', isMenuOpen ? 'block bg-gray-200 text-black p-6 space-y-2 absolute top-16 left-0 w-full' : 'hidden md:static']">
              <li><a href="#" class="hover:text-gray-500">Home</a></li>
              <li><a href="#" class="hover:text-gray-500">About</a></li>
              <li><a href="#" class="hover:text-gray-500">Services</a></li>
              <li><a href="#" class="hover:text-gray-500">Contact</a></li>
            </ul>

            <!-- Search & Language Icons -->
            <img :src="isScrolled ? '../src/assets/white-search.svg' : '../src/assets/black-search.svg'" width="25" height="25">
            <div class="relative flex items-center">
              <img :src="isScrolled ? '../src/assets/white-earth.png' : '../src/assets/black-earth.png'" class="text-gray-500">
              <span class="absolute top-[-8px] right-[-2px] text-[10px] text-blue-500 font-semibold">EN</span>
            </div>

            <!-- Hamburger Button -->
            <button @click="toggleMenu" class="md:hidden flex flex-col justify-center w-8 h-8 space-y-1 focus:outline-none">
              <span :class="['block w-full h-1 rounded transition-all', isScrolled ? 'bg-white' : 'bg-black', isMenuOpen ? 'rotate-45 translate-y-2' : '']"></span>
              <span :class="['block w-full h-1 rounded transition-all', isScrolled ? 'bg-white' : 'bg-black', isMenuOpen ? 'opacity-0' : '']"></span>
              <span :class="['block w-full h-1 rounded transition-all', isScrolled ? 'bg-white' : 'bg-black', isMenuOpen ? '-rotate-45 -translate-y-2' : '']"></span>
            </button>
          </div>
        </div>
      </div>

      <!-- Hero Section -->
      <div class="relative mx-auto text-center max-w-2xl py-64">
        <h1 class="text-4xl sm:text-5xl font-bold mb-6">UNLOCK YOUR BUSINESS POTENTIAL</h1>
        <p class="text-lg sm:text-xl mb-6">
          Strategic Consulting To Elevate Your Business Heights <br>
          Efficient, Secure, and Reliable Way of Doing Business.
        </p>
        <button class="bg-blue-900 hover:bg-gray-600 text-white font-semibold py-3 px-6 rounded-lg">
          Learn More
        </button>
      </div>
    </div>
  </section>
</template>
