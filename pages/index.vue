<template>
    <div class="homepage flex flex-col items-center justify-center min-h-screen bg-gradient-to-r from-blue-200 to-blue-300">
        <h1 class="text-5xl md:text-4xl sm:text-3xl font-extrabold text-gray-800 mb-8 shadow-text animate-pulse">Chinnapat</h1>
        <h1 class="text-5xl md:text-4xl sm:text-3xl font-extrabold text-gray-800 mb-8 shadow-text animate-pulse">Portfolio</h1>
        <img src="@/public/Chinnapat photo.jpg" class="w-1/2 md:w-3/4 sm:w-full h-auto mx-auto block border-gradient hover:scale-105 transition-transform duration-500">
        <p class="text-lg md:text-base sm:text-sm text-gray-700 mt-4 shadow-text text-center">Step into my world of coding, game development, and creative projects.
Explore my work, and let’s make something incredible together!</p>
<div class="inline-flex space-x-4 mt-6">
  <button @click="goToAbout" class="px-5 py-2 md:px-4 md:py-2 sm:px-3 sm:py-1 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700 hover:shadow-lg transition duration-300 hover:scale-110">View About Me</button>
  <button @click="goToProjects" class="px-5 py-2 md:px-4 md:py-2 sm:px-3 sm:py-1 bg-green-500 text-white font-semibold rounded-lg shadow-md hover:bg-green-700 hover:shadow-lg transition duration-300 hover:scale-110">View Projects</button>
</div>

    </div>
</template>

<script setup>
useHead({
    title: 'Chinnapat Portfolio',
    meta: [
        {
            name: 'description',
            content: 'Chinnapat Boonyod Portfolio Website'
        },
        {
            name: 'keywords',
            content: 'Chinnapat, Boonyod, Portfolio, Website, Vue.js, Tailwind CSS, Vite'
        }
    ]
});
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();
const goToAbout = () => {
    router.push('/about');
};
const goToProjects = () => {
    router.push('/projects');
};
</script>

<style scoped>
.homepage {
    animation: fadeIn 1s ease-in-out;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background: linear-gradient(to right, #bfdbfe, #93c5fd);
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

button {
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

.shadow-text {
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.border-gradient {
    border: 5px solid;
    border-image-slice: 1;
    border-width: 5px;
    border-image-source: linear-gradient(to right, #4facfe, #00f2fe);
    transition: transform 0.5s;
}

.border-gradient:hover {
    transform: rotate(5deg);
    filter: brightness(1.1);
}

img {
    border-radius: 0;
    box-shadow: none;
    transition: none;
}

img:hover {
    box-shadow: none;
}

@media (max-width: 1024px), (max-width: 768px), (max-width: 480px) {
    .homepage {
        padding: 20px;
    }

    h1 {
        font-size: 4xl;
    }

    img {
        width: 75%;
        height: auto;
    }

    p {
        font-size: 1rem;
    }

    button {
        width: auto;
        padding: 10px;
    }
}

@media (max-width: 768px), (max-width: 480px) {
    h1 {
        font-size: 3xl;
    }

    img {
        width: 75%;
        height: auto;
    }

    p {
        font-size: 0.875rem;
    }

    button {
        width: 100%;
        padding: 8px;
    }
}

@media (max-width: 480px) {
    h1 {
        font-size: 2xl;
    }

    img {
        width: 100%;
        height: auto;
    }

    p {
        font-size: 0.75rem;
    }

    button {
        width: 100%;
        padding: 6px;
    }
}
</style>