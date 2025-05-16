<template>
  <header class="w-full bg-white shadow-sm fixed top-0 left-0 z-50">
    <div class="max-w-7xl mx-auto flex justify-between items-center px-4 py-6">
      <!-- Logo -->
      <div class="flex items-center space-x-3">
        <img src="@/assets/mevsim.png" alt="Mevsim. Logo" class="w-10 h-10 object-contain" />
        <a href="#" class="text-3xl font-extrabold text-gray-800">Mevsim.</a>
      </div>

      <!-- Navigation -->
      <nav class="hidden md:flex space-x-8">
        <a href="#" class="text-gray-600 hover:text-gray-900 font-medium transition">Ana Sayfa</a>
        <a href="#" class="text-gray-600 hover:text-gray-900 font-medium transition">Ürünler</a>
        <a href="#" class="text-gray-600 hover:text-gray-900 font-medium transition">İletişim</a>
      </nav>

      <!-- Mobile Menu Button -->
      <div class="md:hidden flex items-center">
        <button @click="toggleMobileMenu" class="text-gray-700 hover:text-gray-900 focus:outline-none">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" stroke-width="2"
            viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
            <path d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
        </button>
      </div>
    </div>

    <!-- Mobile Menu -->
    <div v-if="isMobileMenuOpen" class="md:hidden bg-white shadow-md">
      <nav class="flex flex-col p-4 space-y-2">
        <a href="#" class="text-gray-600 hover:text-gray-900 font-medium transition">Ana Sayfa</a>
        <a href="#" class="text-gray-600 hover:text-gray-900 font-medium transition">Ürünler</a>
        <a href="#" class="text-gray-600 hover:text-gray-900 font-medium transition">İletişim</a>
      </nav>
    </div>
  </header>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const isMobileMenuOpen = ref(false);

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};
</script>
