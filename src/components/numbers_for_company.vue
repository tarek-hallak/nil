<script setup>
import { ref, onMounted } from 'vue';

const counters = ref([
  { value: 12416, label: 'LINES OF CODE' },
  { value: 365, label: 'CUPS OF COFFEE' },
  { value: 114, label: 'FINISHED PROJECTS' },
  { value: 14825, label: 'SATISFIED CLIENTS' }
]);

const animatedValues = ref(counters.value.map(() => 0));

onMounted(() => {
  counters.value.forEach((item, index) => {
    let start = 0, duration = 2000;
    let step = () => {
      let progress = Math.min((performance.now() - start) / duration, 1);
      animatedValues.value[index] = Math.floor(progress * item.value);
      if (progress < 1) requestAnimationFrame(step);
    };
    start = performance.now();
    requestAnimationFrame(step);
  });
});
</script>

<template>
  <div class="flex flex-col items-center w-full p-4">
    <div class="overflow-hidden w-full max-w-4xl">
      <div
        class="flex transition-transform duration-500 ease-in-out"
        :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
      >
        <div v-for="(logo, index) in logos" :key="index" class="w-full flex-shrink-0 flex justify-center">
          <img :src="logo.src" :alt="logo.alt" class="h-16 md:h-24 object-contain" />
        </div>
      </div>
    </div>
    <div class="flex space-x-2 mt-4">
      <button
        v-for="(logo, index) in logos"
        :key="index"
        @click="currentIndex = index"
        class="h-3 w-3 rounded-full"
        :class="currentIndex === index ? 'bg-gray-800' : 'bg-gray-400'"
      ></button>
    </div>
  </div>
</template>
