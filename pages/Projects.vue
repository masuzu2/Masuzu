<template>
    <div class="min-h-screen bg-gradient-to-r from-blue-100 to-blue-200 flex flex-col items-center justify-center py-12">
      <h1 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-extrabold mb-8 text-transparent bg-clip-text bg-gradient-to-r from-blue-300 to-blue-500 leading-tight animate-bounce">
        Projects
      </h1>
  
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 sm:gap-6 md:gap-8">
        <!-- Loop through projects -->
        <div v-for="project in projects" :key="project.id" class="project-card bg-white p-4 sm:p-6 rounded-lg shadow-2xl transform transition duration-500 hover:scale-105 hover:shadow-3xl">
          <h2 class="text-xl sm:text-2xl md:text-3xl font-bold mb-2 text-blue-300 leading-snug">{{ project.title }}</h2>
          <p class="text-gray-700 text-sm sm:text-base mb-4">
            {{ project.description }}
          </p>
  
          <!-- Placeholder for project image -->
          <div class="flex justify-center items-center bg-gray-300 p-4 rounded-md mb-4">
            <span class="text-gray-600 font-semibold"></span>
          </div>
  
          <!-- Animated text to highlight the project -->
          <div class="animate-pulse text-blue-500 font-bold text-lg text-center">
            Check out the amazing Full Stack Project!
          </div>
          
          <button class="mt-4 px-3 sm:px-4 py-2 bg-blue-300 text-white rounded-lg shadow-md hover:bg-blue-400 transition duration-300">
            Learn More
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  const projects = [
    {
      id: 1,
      title: 'Full Stack Developer',
      description: 'This is a simple Full Stack Developer project. It includes backend, frontend, and a working API connected to MongoDB.',
    },
  ];
  </script>
  
  <style lang="scss" scoped>
  .project-card {
    animation: fadeIn 1s ease-in-out, pulse 2s infinite;
    border: 1px solid #e0e0e0;
    transition: transform 0.3s, box-shadow 0.3s;
  }
  
  .project-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  }
  
  @keyframes fadeIn {
    from {
      opacity: 0;
      transform: translateY(-20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  
  @keyframes pulse {
    0%, 100% {
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    50% {
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
    }
  }
  
  h1 {
    animation: bounce 2s infinite;
  }
  
  @keyframes bounce {
    0%, 20%, 50%, 80%, 100% {
      transform: translateY(0);
    }
    40% {
      transform: translateY(-30px);
    }
    60% {
      transform: translateY(-15px);
    }
  }
  
  pre {
    max-height: 200px;
    overflow-y: auto;
    font-size: 14px;
  }
  
  /* Animated text style */
  .animate-pulse {
    animation: pulse 2s infinite;
  }
  </style>
  