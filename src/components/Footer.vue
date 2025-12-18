<template>
  <footer class="bg-gray-950 text-gray-300 pt-12 pb-6">
    <div class="container mx-auto px-4">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 mb-8">
        <div>
          <h3 class="text-xl font-bold text-white mb-4">Scent Haven</h3>
          <p class="mb-4">
            Your premier destination for luxury fragrances from around the
            world.
          </p>
          <div class="flex space-x-4">
            <a
              v-for="(social, index) in socialLinks"
              :key="index"
              :href="social.link"
              class="text-gray-400 hover:text-white transition"
            >
              <Icon :icon="social.icon" class="w-5 h-5" />
            </a>
          </div>
        </div>

        <!-- Quick Links -->
        <div>
          <h3 class="text-lg font-semibold text-white mb-4">Quick Links</h3>
          <ul class="space-y-2">
            <li v-for="(link, index) in quickLinks" :key="index">
              <a href="#" class="hover:text-white transition">{{ link }}</a>
            </li>
          </ul>
        </div>

        <!-- Customer Service -->
        <div>
          <h3 class="text-lg font-semibold text-white mb-4">
            Customer Service
          </h3>
          <ul class="space-y-2">
            <li v-for="(service, index) in custromerService" :key="index">
              <a href="#" class="hover:text-white transition">{{ service }}</a>
            </li>
          </ul>
        </div>

        <!-- Newsletter -->
        <div>
          <h3 class="text-lg font-semibold text-white mb-4">Newsletter</h3>
          <p class="mb-4">
            Subscribe to our newsletter for updates and offers.
          </p>
          <form class="flex">
            <input
              type="email"
              placeholder="Your email"
              class="px-4 py-2 w-full rounded-l-lg focus:outline-none text-gray-700 border"
            />
            <button
              type="submit"
              class="bg-pink-600 hover:bg-pink-700 text-white px-4 py-2 rounded-r-lg transition"
            >
              Subscribe
            </button>
          </form>
          <div class="mt-4 flex items-center">
            <Icon icon="fa-solid:envelope" class="w-5 h-5 mr-2" />
            <span>support@scenthaven.com</span>
          </div>
        </div>
      </div>

      <!-- Footer Bottom -->
      <div
        class="border-t border-gray-800 pt-6 flex flex-cols md:flex-row justify-between items-center"
      >
        <p>
          &copy; {{ new Date().getFullYear() }} Scent Haven. All rights
          reserved.
        </p>
        <div class="flex space-x-6 mt-4 md:mt-0">
          <Icon
            v-for="(icon, index) in paymentIcons"
            :key="index"
            :icon="icon"
            class="w-8 h-8"
          />
        </div>
      </div>
    </div>
  </footer>
</template>
<script setup>
import { ref } from "vue";
const quickLinks = ref([
  "Home",
  "Shop",
  "New Arrivals",
  "Best Sellers",
  "Gift Sets",
]);
const custromerService = ref([
  "Contact Us",
  "Shipping & Returns",
  "FAQ",
  "Privacy Policy",
  "Terms of Service",
]);
const paymentIcons = ref([
  "logos:visa",
  "logos:mastercard",
  "logos:paypal",
  "logos:amex",
]);
const socialLinks = ref([
  { icon: "mdi:facebook", link: "https://facebook.com" },
  { icon: "mdi:twitter", link: "https://twitter.com" },
  { icon: "mdi:instagram", link: "https://instagram.com" },
  { icon: "mdi:pinterest", link: "https://pinterest.com" },
]);
</script>
