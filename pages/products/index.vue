<template>
    <div class="min-h-screen bg-gradient-to-r from-blue-200 via-purple-200 to-pink-200 flex flex-col items-center justify-center">
      <h1 class="text-6xl font-extrabold mb-12 text-transparent bg-clip-text bg-gradient-to-r from-blue-500 to-purple-500">Products for Web</h1>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <!-- Render each product dynamically using v-for -->
        <a 
          v-for="product in products" 
          :key="product.id" 
          :href="product.link" 
          class="product-card bg-white p-6 rounded-lg shadow-lg transform transition duration-500 hover:scale-105 hover:shadow-2xl">
          <div class="product-image mb-4">
            <img :src="product.image" :alt="product.name" class="w-full h-48 object-cover rounded-t-lg" />
          </div>
          <h2 class="text-2xl font-bold mb-2 text-blue-400">{{ product.name }}</h2>
          <p class="text-gray-700 mb-4">{{ product.description }}</p>
          <button class="add-to-cart-btn bg-blue-500 text-white py-2 px-4 rounded-full transition duration-300 hover:bg-blue-600">Add to Cart</button>
        </a>
        <!-- Add more product cards as needed -->
      </div>
    </div>
    <div class="flex flex-wrap justify-center space-x-2 sm:space-x-4">
    </div>
  </template>
  
  <script setup>
  useHead({
    title: 'Products for Web',
    meta: [
      {
        name: 'description',
        content: 'Web Products'
      },
      {
        name: 'keywords',
        content: 'Web, Products, Vue.js, Tailwind CSS, Vite'
      }
    ]
  });
  
  const products = [
    { 
      id: 1, 
      name: 'TOUGH GEAR INTERNATIONAL TEE', 
      image: '/images/t-shirt1.webp', 
      description: 'Oversized tee in midweight 6.5oz cotton jersey. Features screenprinted graphics.', 
      link: 'https://www.stussy.com/collections/tees/products/1905101-tough-gear-international-tee-black' 
    },
    { 
      id: 2, 
      name: '8 BALL HOODIE PIGMENT DYED', 
      image: '/images/HOODIE1.webp', 
      description: 'Oversized pigment dyed hoodie in heavy 14oz cotton fleece with a brushed interior. Screenprinted using water-based ink for a soft hand feel.', 
      link: 'https://www.stussy.com/collections/hoodies/products/1925022-8-ball-hoodie-pigment-dyed-khaki' 
    },
    { 
      id: 3, 
      name: 'BASIC STÜSSY HOODIE', 
      image: '/images/HOODIE2.webp', 
      description: 'Oversized hooded sweatshirt in a heavy 12.7oz cotton blend. Screenprinted Stüssy basic stock logo.', 
      link: 'https://www.stussy.com/collections/hoodies/products/1925000-basic-stussy-hoodie-ash-heather' 
    }
    // Add more products as needed
  ];
  </script>
  
  <style lang="scss" scoped>
  .product-card {
    position: relative;
    overflow: hidden;
    transition: transform 0.3s, box-shadow 0.3s;
    display: block;
    text-decoration: none;
    color: inherit;
    border-radius: 1rem;
    background: linear-gradient(135deg, #ffffff 0%, #f0f0f0 100%);
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    animation: fadeIn 1s ease-in-out, pulse 2s infinite;
  }
  
  .product-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, rgba(70, 130, 180, 0.1) 0%, rgba(70, 130, 180, 0) 100%);
    opacity: 0;
    transition: opacity 0.3s;
  }
  
  .product-card:hover::before {
    opacity: 1;
  }
  
  .product-card:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  }
  
  .product-image {
    border-bottom: 1px solid #eaeaea;
    transition: transform 0.3s;
  }
  
  .product-card:hover .product-image {
    transform: scale(1.1);
  }
  
  .add-to-cart-btn {
    display: block;
    width: 100%;
    text-align: center;
    font-weight: bold;
    margin-top: auto;
    background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: background-color 0.3s, box-shadow 0.3s;
  }
  
  .add-to-cart-btn:hover {
    background-color: #1d4ed8;
    box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
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
  
  /* Responsive Design */
  @media (max-width: 768px) {
    .product-card {
      padding: 16px;
    }
    .product-image img {
      height: 200px;
    }
    .add-to-cart-btn {
      padding: 12px;
    }
  }
  
  @media (max-width: 480px) {
    .product-card {
      padding: 8px;
    }
    .product-image img {
      height: 150px;
    }
    .add-to-cart-btn {
      padding: 8px;
    }
  }
  </style>
  