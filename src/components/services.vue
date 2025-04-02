<script setup>
const services = [
  { icon: 'fas fa-plug', title: 'Powerful Template' },
  { icon: 'fas fa-desktop', title: 'Flexible Layouts' },
  { icon: 'fas fa-cloud', title: 'Retina Ready' },
  { icon: 'fas fa-lightbulb', title: 'Fast Processing' },
  { icon: 'fas fa-trophy', title: 'Unlimited Colors' },
  { icon: 'fas fa-thumbs-up', title: 'Premium Sliders' },
  { icon: 'fas fa-rocket', title: 'Modern Design' },
  { icon: 'fas fa-scissors', title: 'Modern Design' },
  { icon: 'fas fa-umbrella', title: 'Free Updates & Support' },
];
</script>

<style>
/* Add FontAwesome Icons (if not included globally) */
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css');
</style>

<template>
  <section class="py-16 bg-white">
    <div class="container mx-auto px-6 text-center">
      <!-- Heading -->
      <h2 class="text-4xl font-bold text-gray-900">Services</h2>
      <p class="mt-2 text-gray-500 max-w-2xl mx-auto text-lg">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse condimentum porttitor cursusmus.
      </p>

      <!-- Services Grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-16 mt-10">
        <div v-for="(service, index) in services" :key="index" class="flex items-start space-x-4 ">
          <!-- Icon -->
          <div class="flex items-center justify-center  p-8 h-16 w-16 border-2  border-gray-800 rounded-full shadow-lg">
            <i :class="service.icon" class="text-2xl text-gray-800"></i>
          </div>
          <!-- Content -->
          <div class="text-left">
            <h3 class="text-xl font-semibold text-gray-900">{{ service.title }}</h3>
            <p class="text-gray-500 ">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse condimentum.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
