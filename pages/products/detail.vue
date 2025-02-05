<template>
    <div class="min-h-screen bg-gray-200 flex flex-col items-center justify-center">
        <h1 class="text-5xl font-bold mb-8 text-blue-500">Detail for Products</h1>
        <div class="product-detail-card bg-white p-6 rounded-lg shadow-lg transform transition duration-500 hover:scale-105 hover:shadow-2xl">
            <div class="product-image mb-4">
                <img src="https://via.placeholder.com/300" alt="Product Image" class="w-full h-64 object-cover rounded-t-lg">
            </div>
            <h2 class="text-2xl font-bold mb-2 text-blue-400">Product Title</h2>
            <p class="text-gray-700 mb-4">Detailed product description goes here.</p>
            <button class="add-to-cart-btn bg-blue-500 text-white py-2 px-4 rounded-full transition duration-300 hover:bg-blue-600">Add to Cart</button>
        </div>
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.product-detail-card {
    position: relative;
    overflow: hidden;
    transition: transform 0.3s, box-shadow 0.3s;
    display: block;
    text-decoration: none;
    color: inherit;
    border-radius: 1rem;
}

.product-detail-card::before {
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

.product-detail-card:hover::before {
    opacity: 1;
}

.product-detail-card:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.product-image {
    border-bottom: 1px solid #eaeaea;
}

.add-to-cart-btn {
    display: block;
    width: 100%;
    text-align: center;
    font-weight: bold;
    margin-top: auto;
}

.add-to-cart-btn:hover {
    background-color: #2563eb;
}

@media (max-width: 768px) {
    .product-detail-card {
        padding: 4rem 2rem;
    }

    .product-image img {
        height: auto;
    }

    .add-to-cart-btn {
        padding: 1rem;
    }
}

@media (max-width: 480px) {
    .product-detail-card {
        padding: 2rem 1rem;
    }

    .product-image img {
        height: auto;
    }

    .add-to-cart-btn {
        padding: 0.75rem;
    }
}
</style>