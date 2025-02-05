<template>
    <div class="min-h-screen bg-gradient-to-br from-blue-100 via-blue-200 to-blue-300 text-gray-800 font-['Comic_Sans_MS']">
      <header class="relative z-10">
        <nav class="relative mx-auto my-2.5 flex flex-wrap items-center justify-between rounded-lg bg-gradient-to-r from-blue-200 to-blue-300 px-5 py-2.5 shadow-lg overflow-hidden max-w-7xl">
          <!-- Decorative overlay elements -->
          <div class="absolute inset-0 bg-blue-100/10 -skew-x-12 transform transition-transform duration-500 ease-in-out hover:translate-x-full"></div>
          <div class="absolute inset-0 bg-blue-200/20 -skew-x-12 transform transition-transform duration-500 -translate-x-full ease-in-out hover:translate-x-full"></div>
          <div class="absolute inset-0 bg-gradient-to-r from-blue-300 to-blue-400 opacity-50 rounded-lg blur-lg"></div>
          
          <!-- Logo -->
          <h1 class="mr-auto pl-2.5 font-['Pacifico'] text-2xl sm:text-3xl text-gray-800 animate-pulse shadow-sm relative">
            <span class="relative z-10">Masuzu</span>
            <span class="absolute inset-0 text-blue-300 blur-sm">Masuzu</span>
          </h1>
  
          <!-- Navigation Links -->
          <div class="flex flex-wrap justify-center space-x-2 sm:space-x-4">
            <NuxtLink 
              v-for="(link, index) in links" 
              :key="index"
              :to="link.to"
              class="group relative px-2 py-1 sm:px-4 sm:py-2.5 text-sm sm:text-lg font-bold text-gray-800 transition-all duration-300 ease-in-out hover:scale-110 hover:text-blue-400 hover:drop-shadow-[0_0_10px_rgba(173,216,230,0.8)] text-center"
            >
              {{ link.text }}
              <span class="absolute bottom-0 left-0 h-0.5 w-full origin-right scale-x-0 bg-gray-800 transition-transform duration-300 ease-in-out group-hover:origin-left group-hover:scale-x-100"></span>
            </NuxtLink>
          </div>
        </nav>
      </header>
      <div class="relative z-0 mx-auto mt-5 max-w-7xl p-5 bg-white bg-opacity-10 rounded-lg shadow-2xl backdrop-blur-md">
        <slot />
      </div>
    </div>
  </template>
  
  <script setup>
  const links = [
    { text: 'Home', to: '/' },
    { text: 'About Us', to: '/about' },
    { text: 'Projects', to: '/projects' },
    { text: 'Contact', to: '/Contact' },
    { text: 'Products', to: '/products' }
  ]
  </script>
  
  <style>
  @keyframes pulse {
    0% {
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5), 0 0 10px #add8e6, 0 0 20px #add8e6, 0 0 30px #add8e6;
    }
    100% {
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5), 0 0 20px #add8e6, 0 0 30px #add8e6, 0 0 40px #add8e6;
    }
  }
  
  .animate-pulse {
    animation: pulse 1.5s infinite alternate;
  }
  </style>