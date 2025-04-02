<script>
// JavaScript to handle scroll behavior
window.addEventListener('scroll', () => {
  const navbar = document.querySelector('#nav');
  const logo = document.querySelector('#logo');
  const searchIcon = document.querySelector('#searchIcon');
  const earthIcon = document.querySelector('#earthIcon');
  if (window.scrollY > 50) {
    navbar.classList.add('bg-black', 'text-white');
    navbar.classList.remove('bg-transparent', 'text-black');
    logo.src = '../src/assets/white-logo.png'; // Switch to white logo
    searchIcon.src = '../src/assets/white-search.svg'
    earthIcon.src = '../src/assets/white-earth.png'
  } else {
    navbar.classList.add('bg-transparent', 'text-black');
    navbar.classList.remove('bg-black', 'text-white');
    logo.src = '../src/assets/black-logo.png'; // Switch to black logo
    searchIcon.src = '../src/assets/black-search.svg'
    earthIcon.src = '../src/assets/black-earth.png'
  }
});
// JavaScript to handle the hamburger action
document.addEventListener('DOMContentLoaded', () => {
  const menuToggle = document.getElementById('menu-toggle');
  const menu = document.getElementById('menu');
  const line1 = document.getElementById('line-1');
  const line2 = document.getElementById('line-2');
  const line3 = document.getElementById('line-3');

  if (!menuToggle || !menu || !line1 || !line2 || !line3) {
    console.error('One or more required elements are missing in the DOM.');
    return; // Stop execution if elements are missing
  }

  // Toggle menu open/close
  menuToggle.addEventListener('click', () => {
    const isHidden = menu.classList.contains('hidden');
    menu.classList.toggle('hidden');

    if (isHidden) {
      line1.classList.add('transform', 'rotate-45', 'translate-y-2');
      line2.classList.add('opacity-0');
      line3.classList.add('transform', '-rotate-45', '-translate-y-2');
    } else {
      line1.classList.remove('transform', 'rotate-45', 'translate-y-2');
      line2.classList.remove('opacity-0');
      line3.classList.remove('transform', '-rotate-45', '-translate-y-2');
    }
  });

  // Scroll behavior for hamburger lines
  window.addEventListener('scroll', () => {
    const isScrolled = window.scrollY > 50;

    // Change only the hamburger lines to white
    if (isScrolled) {
      line1.classList.replace('bg-black', 'bg-white'); // Replace black with white
      line2.classList.replace('bg-black', 'bg-white');
      line3.classList.replace('bg-black', 'bg-white');
    } else {
      line1.classList.replace('bg-white', 'bg-black'); // Replace white with black
      line2.classList.replace('bg-white', 'bg-black');
      line3.classList.replace('bg-white', 'bg-black');
    }
  });
});
</script>

<template>
  <section>
    <!-- display the image background -->
    <div class="overflow-hidden bg-[url('hero.jpg')] bg-cover bg-center bg-no-repeat h-screen w-full m-0">
      <div class="fixed top-0 left-0 w-full z-50 bg-transparent text-gray-900 transition-all duration-300">
        <div id="nav" class="flex justify-around items-center px-6 py-4">

          <!-- Logo -->
          <div>
            <img id="logo" src="../assets/black-logo.png" alt="Logo" class="h-10 relative z-10">
          </div>
          <div class="flex gap-4 ">
            <!-- Menu Items -->
            <ul id="nav"
              class="hidden md:flex md:space-x-6 items-center text-lg absolute md:static top-16 left-0 w-full bg-gray-200 md:bg-transparent p-6 md:p-0  font-bold">
              <li><a href="#" class="block px-4 py-2 hover:text-gray-500">Home</a></li>
              <li><a href="#" class="block px-4 py-2 hover:text-gray-500">About</a></li>
              <li><a href="#" class="block px-4 py-2 hover:text-gray-500">Services</a></li>
              <li><a href="#" class="block px-4 py-2 hover:text-gray-500">Contact</a></li>
            </ul>
            <!-- search icon -->
            <img id="searchIcon" src="../assets/black-search.svg" width="25" height="25" class="">
            <!-- language icon -->
            <div class="relative flex items-center">
              <img id="earthIcon" class=" text-gray-500" src="../assets/black-earth.png"></img>
              <span
                class="absolute top-[-8px] right-[-2px] text-[10px] opacity-100 text-blue-500 font-semibold">EN</span>
            </div>

            <!-- Hamburger Button -->
            <button id="menu-toggle"
              class="flex flex-col justify-center w-8 h-8 space-y-1 md:hidden focus:outline-none">
              <span class="block w-full h-1 bg-black rounded transition-transform duration-300 ease-in-out"
                id="line-1"></span>
              <span class="block w-full h-1 bg-black rounded transition-opacity duration-300 ease-in-out"
                id="line-2"></span>
              <span class="block w-full h-1 bg-black rounded transition-transform duration-300 ease-in-out"
                id="line-3"></span>
            </button>

          </div>
        </div>
      </div>
      <!-- Hero -->
      <div class="relative mx-auto text-center max-w-2xl py-64">
        <h1 class="text-4xl sm:text-5xl font-bold mb-6">UNLOCK YOUR BUSINESS POTENTIAL</h1>
        <p class="text-lg sm:text-xl  mb-6">
          Strategic Consulting To Elevate Your Business Heights <br />
          Efficient, Secure, and Reliable Way of Doing Business.
        </p>
        <button class="bg-blue-900 hover:bg-gray-600 text-white font-semibold py-3 px-6 rounded-lg ">
          Learn More
        </button>
      </div>
    </div>
  </section>



</template>
