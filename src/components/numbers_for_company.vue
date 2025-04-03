<script setup>
import { ref, onMounted } from 'vue';

const counters = ref([
  { value: 12416, label: 'LINES OF CODE' },
  { value: 365, label: 'CUPS OF COFFEE' },
  { value: 114, label: 'FINISHED PROJECTS' },
  { value: 14825, label: 'SATISFIED CLIENTS' }
]);

const animatedValues = ref(counters.value.map(() => 0));
const hasAnimated = ref(false);
const counterSection = ref(null);

const startCounterAnimation = () => {
  if (hasAnimated.value) return; // Prevent multiple animations
  hasAnimated.value = true;

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
};

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      if (entries[0].isIntersecting) {
        startCounterAnimation();
      }
    },
    { threshold: 0.5 } // Trigger when 50% of the section is visible
  );

  if (counterSection.value) {
    observer.observe(counterSection.value);
  }
});
</script>

<template>
  <div class="bg-gray-100">
    <div class="container mx-auto p-24">
      <div ref="counterSection" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 text-center">
        <div v-for="(item, index) in counters" :key="index">
          <p class="text-gray-600 font-bold text-6xl">{{ animatedValues[index] }}</p>
          <p class="mt-6 font-light text-xl">{{ item.label }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
