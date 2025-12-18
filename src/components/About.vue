<template>
  <div
    id="about"
    class="scroll-mt-20 bg-linear-to-b from-gray-50 to-white py-12 px-4 sm:px-6 lg:px-8"
  >
    <div class="max-w-7xl mx-auto">
      <div class="flex flex-col lg:flex-row gap-12 mb-20">
        <!-- Image Section -->
        <div class="lg:w-1/2">
          <div class="relative rounded-2xl overflow-hidden h-96 shadow-xl">
            <img
              :src="product1"
              alt="luxury perfumes"
              class="w-full h-full object-cover"
            />
            <div
              class="absolute inset-0 bg-linear-to-t from-black to-transparent opacity-50"
            >
              <!-- <h2 class="text-white text-3xl font-bold">About Our Luxury Perfumes</h2> -->
            </div>
            <div class="absolute botton-0 left-0 p-6 text-white">
              <h3 class="text-2xl font-bold">Since 2024</h3>
              <p class="mt-2">Craft perfumes with passion</p>
            </div>
          </div>
        </div>

        <!-- Text Content -->
        <div class="lg:w-1/2 flex flex-col justify-center">
          <h2 class="text-4xl font-bold text-amber-900 mb-6">About Us</h2>
          <p class="text-lg text-gray-600 mb-4">
            At LuxeScents, we believe that a fragrance is more than just a
            scent; it's an expression of individuality and a journey of the
            senses. Since our founding in 2024, we've been dedicated to crafting
            exquisite perfumes that captivate and inspire.
          </p>
          <div class="grid grid-cols-2 gap-4 mt-4">
            <div
              class="bg-white p-4 rounded-lg shadow-sm border border-gray-100"
            >
              <h4 class="font-semibold text-pink-600">500+</h4>
              <p class="text-gray-600">Unique fragrance</p>
            </div>
            <div
              class="bg-white p-4 rounded-lg shadow-sm border border-gray-100"
            >
              <h4 class="font-semibold text-pink-600">50+</h4>
              <p class="text-gray-600">Countries worldwide</p>
            </div>
            <div
              class="bg-white p-4 rounded-lg shadow-sm border border-gray-100"
            >
              <h4 class="font-semibold text-pink-600">100+</h4>
              <p class="text-gray-600">Customer satifaction</p>
            </div>
            <div
              class="bg-white p-4 rounded-lg shadow-sm border border-gray-100"
            >
              <h4 class="font-semibold text-pink-600">24/7</h4>
              <p class="text-gray-600">Customer support</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import product1 from "../assets/product.jpg";
</script>
