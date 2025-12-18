<template>
  <section id="products" class="py-12 scroll-mt-20 bg-gray-50">
    <main class="container mx-auto px-4">
      <!-- Header -->
      <header class="flex justify-between items-center mb-8">
        <h2 class="md:text-3xl text-2xl font-bold text-amber-900">
          Featured Products
        </h2>
        <nav class="flex space-x-4" aria-label="Product carousel controls">
          <button
            @click="prevSlide"
            class="p-2 rounded-full bg-white shadow-md hover:bg-pink-100 text-pink-600 transition-colors"
            aria-label="Previous Slide"
          >
            <Icon icon="line-md:arrow-small-left" width="24" height="24" />
          </button>
          <button
            @click="nextSlide"
            class="p-2 rounded-full bg-white shadow-md hover:bg-pink-100 text-pink-600 transition-colors"
            aria-label="Next Slide"
          >
            <Icon icon="line-md:arrow-small-right" width="24" height="24" />
          </button>
        </nav>
      </header>

      <!-- Product Grid -->
      <section class="relative overflow-hidden">
        <ul
          class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6"
        >
          <li
            v-for="product in visibleSlides"
            :key="product.id"
            class="bg-white rounded-lg shadow-md overflow-hidden transition-all duration-300 hover:scale-105"
          >
            <article>
              <!-- Image Section -->
              <figure class="relative">
                <img
                  :src="product.image"
                  :alt="product.name"
                  class="w-full h-64 object-cover"
                />
                <figcaption
                  v-if="product.discount > 0"
                  class="absolute top-3 right-3 bg-red-500 text-white text-xs font-bold px-2 py-1 rounded-full"
                >
                  -{{ product.discount }}%  
                </figcaption>
                <button
                  class="absolute top-3 left-3 p-2 bg-white rounded-full shadow-md hover:bg-pink-100 text-gray-700"
                  aria-label="Add to Wishlist"
                >
                  <Icon icon="line-md:heart" width="18" height="18" />
                </button>
              </figure>

              <!-- Info Section -->
              <section class="p-4">
                <div class="flex items-center mb-2">
                  <Icon
                    v-for="i in 5"
                    :key="i"
                    icon="line-md:star-alt-filled"
                    width="16"
                    height="16"
                    :class="
                      i <= Math.floor(product.rating)
                        ? 'text-yellow-400'
                        : 'text-gray-300'
                    "
                  />
                  <span class="text-sm text-gray-500 ml-1">
                    ({{ product.rating }})
                  </span>
                </div>

                <h3 class="text-lg font-semibold text-gray-800 mb-1">
                  {{ product.name }}
                </h3>

                <footer class="flex items-center justify-between">
                  <div>
                    <span class="text-lg font-bold text-pink-600">
                      ${{
                        (product.price * (1 - product.discount / 100)).toFixed(
                          2
                        )
                      }}
                    </span>
                    <span
                      v-if="product.discount > 0"
                      class="text-sm text-gray-500 line-through ml-2"
                    >
                      ${{ product.price.toFixed(2) }}
                    </span>
                  </div>

                  <button
                    class="p-2 bg-pink-950 rounded-full text-white hover:bg-pink-700 transition-colors"
                    aria-label="Add to Cart"
                  >
                    <Icon
                      icon="icon-park-solid:shopping"
                      width="18"
                      height="18"
                    />
                  </button>
                </footer>
              </section>
            </article>
          </li>
        </ul>
      </section>

      <!-- Pagination Dots -->
      <nav class="flex justify-center mt-6 space-x-2" aria-label="Pagination">
        <button
          v-for="index in totalSlides"
          :key="index"
          @click="currentSlide = index - 1"
          :class="[
            'w-3 h-3 rounded-full',
            currentSlide === index - 1 ? 'bg-pink-950' : 'bg-gray-400',
          ]"
        />
      </nav>
    </main>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onBeforeUnmount } from "vue";
import product1 from "../assets/product.jpg";
import product2 from "../assets/product1.jpg";
import product3 from "../assets/product2.jpg";
import product4 from "../assets/product3.jpg";
import product5 from "../assets/product4.jpg";
import product6 from "../assets/product5.jpg";
import product7 from "../assets/product6.jpg";
import product8 from "../assets/product7.jpg";

const currentSlide = ref(0);
const productsPerPage = ref(4);

const products = [
  {
    id: 1,
    name: "Floral",
    rating: 3.5,
    discount: 20,
    image: product1,
    price: 89.99,
  },
  {
    id: 2,
    name: "Oriental",
    rating: 4.6,
    discount: 25,
    image: product2,
    price: 79.99,
  },
  {
    id: 3,
    name: "Woody",
    rating: 5.0,
    discount: 30,
    image: product3,
    price: 69.99,
  },
  {
    id: 4,
    name: "Citrus",
    rating: 3.8,
    discount: 35,
    image: product4,
    price: 59.99,
  },
  {
    id: 5,
    name: "Fresh",
    rating: 4.4,
    discount: 40,
    image: product5,
    price: 49.99,
  },
  {
    id: 6,
    name: "Spicy",
    rating: 5.0,
    discount: 45,
    image: product6,
    price: 39.99,
  },
  {
    id: 7,
    name: "Herbal",
    rating: 3.8,
    discount: 50,
    image: product7,
    price: 29.99,
  },
  {
    id: 8,
    name: "Musky",
    rating: 4.8,
    discount: 55,
    image: product8,
    price: 19.99,
  },
];

const totalSlides = computed(() =>
  Math.ceil(products.length / productsPerPage.value)
);

const visibleSlides = computed(() => {
  const start = currentSlide.value * productsPerPage.value;
  return products.slice(start, start + productsPerPage.value);
});

const nextSlide = () => {
  currentSlide.value =
    currentSlide.value === totalSlides.value - 1 ? 0 : currentSlide.value + 1;
};

const prevSlide = () => {
  currentSlide.value =
    currentSlide.value === 0 ? totalSlides.value - 1 : currentSlide.value - 1;
};

const handleResize = () => {
  if (window.innerWidth < 640) {
    productsPerPage.value = 1;
  } else if (window.innerWidth < 768) {
    productsPerPage.value = 2;
  } else if (window.innerWidth < 1024) {
    productsPerPage.value = 3;
  } else {
    productsPerPage.value = 4;
  }
};

onMounted(() => {
  handleResize();
  window.addEventListener("resize", handleResize);
});

onBeforeUnmount(() => {
  window.removeEventListener("resize", handleResize);
});
</script>
