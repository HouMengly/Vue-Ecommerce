<template>
  <header class="sticky top-0 z-50 transition-all duration-300">
    <section
      :class="[
        'w-full',
        isScrolled
          ? 'bg-gray-100/95 backdrop-blur shadow-md py-2'
          : 'bg-gray-100 py-4',
      ]"
    >
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div
          class="flex flex-col md:flex-row items-center justify-between gap-3 md:gap-6"
        >
          <!-- logo + mobile manu toggle -->
          <div class="w-full md:w-auto flex justify-between items-center">
            <a href="/" class="text-2xl font-bold text-pink-600">TerkOb</a>
            <button
              class="md:hidden text-gray-700 hover:text-indigo-600"
              aria-label="Toggle mobile menu"
              @click="isMobileMenuOpen = !isMobileMenuOpen"
            >
              <Icon icon="mdi:menu" width="28" height="28" />
            </button>
          </div>

          <!-- Search Bar -->
          <form
            class="w-full md:flex-1 max-w-sm"
            role="search"
            aria-label="Site search"
          >
            <label class="w-full relative">
              <input
                type="text"
                placeholder="Search ..."
                class="w-full px-3 py-3 text-xs border border-gray-300 rounded-full focus:outline-none focus:ring-2 focus:ring-indigo-500"
              />
              <button
                type="submit"
                class="absolute right-2 top-1/2 -translate-1/2 text-gray-500 hover:text-blue-500"
                aria-label="Search button"
              >
                <Icon icon="mdi:magnify" width="24" height="24" />
              </button>
            </label>
          </form>

          <!-- Icons -->
          <aside
            class="w-full md:w-auto flex items-center justify-end space-x-4"
          >
            <button
              class="relative p-2 text-gray-700 hover:text-pink-600"
              aria-label="Wishlish"
            >
              <Icon icon="mdi:heart-outline" width="28" height="28" />
              <span
                class="h-5 w-5 absolute -top-1 -right-1 bg-pink-500 text-white text-xs rounded-full flex items-center justify-center"
                >3</span
              >
            </button>
            <button
              class="relative p-2 text-gray-700 hover:text-pink-600"
              aria-label="Wishlish"
            >
              <Icon icon="mdi:cart-outline" width="28" height="28" />
              <span
                class="h-5 w-5 absolute -top-1 -right-1 bg-pink-500 text-white text-xs rounded-full flex items-center justify-center"
                >5</span
              >
            </button>
            <button
              class="relative p-2 text-gray-700 hover:text-pink-600"
              aria-label="Wishlish"
            >
              <Icon icon="mdi:account-outline" width="28" height="28" />
            </button>
          </aside>
        </div>
      </div>
    </section>

    <!-- Navbar Links -->
    <nav class="bg-pink-950" aria-label="Main navigation">
      <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <ul
          class="hidden md:flex justify-center py-3 flex-wrap gap-x-6 text-sm font-medium text-white"
        >
          <li v-for="item in navItems" :key="item.id">
            <a :href="item.link" class="hover:text-pink-300 transition-colors">
              {{ item.name }}
            </a>
          </li>
        </ul>

        <div
          v-if="isMobileMenuOpen"
          class="md:hidden mt-2 bg-white rounded-lg shadow-md space-y-3 text-[#5D4037] text-center"
          aria-label="Mobile navigation"
        >
          <a
            v-for="item in navItems"
            :href="item.link"
            :key="item.id"
            class="block hover:text-amber-600 text-sm font-medium"
            >{{ item.name }}</a
          >
        </div>
      </section>
    </nav>
  </header>
</template>
<script setup>
import { ref, onMounted, onUnmounted } from "vue";
const isScrolled = ref(false);
const isMobileMenuOpen = ref(false);
const navItems = [
  { id: 1, name: 'Home', link: '#home' },
  { id: 2, name: 'Product', link: '#products' },
  { id: 3, name: 'Categories', link: '#categories' },
  { id: 4, name: 'Offers', link: '#offers' },
  { id: 5, name: 'About', link: '#about' },
  { id: 6, name: 'Contact', link: '#contact' },
];

const handleScroll = () => {
  isScrolled.value = window.scrollY > 10;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>
