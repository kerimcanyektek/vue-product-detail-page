<template>
  <div class="space-y-6">
    <!-- Product Title -->
    <h1 class="text-3xl font-bold text-gray-900">
      {{ title }}
    </h1>

    <!-- Stars -->
    <div class="flex items-center space-x-1 text-yellow-400 text-xl">
      <span>★★★★☆</span>
      <span class="text-sm text-gray-500">(4.5)</span>
    </div>

    <!-- Product Category -->
    <p class="text-gray-600 leading-relaxed">
      {{ category }}
    </p>

    <!-- Product Price -->
    <div class="flex items-center space-x-2">
      <span class="text-3xl font-extrabold text-green-600">
        {{ price }}₺
      </span>
    </div>

    <!-- Buttons -->
    <div class="flex flex-col md:flex-row gap-4">
      <button @click="addToCart"
        class="w-full md:w-auto px-6 py-3 bg-blue-600 hover:bg-blue-700 text-white font-semibold rounded-lg transition">
        Sepete Ekle
      </button>

      <button @click="buyNow"
        class="w-full md:w-auto px-6 py-3 bg-green-600 hover:bg-green-700 text-white font-semibold rounded-lg transition">
        Hemen Al
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  title: string;
  category: string;
  price: number;
}>();

function addToCart() {
  alert('🎉 Ürün sepete eklendi!');
}

function buyNow() {
  alert('🚀 Hemen satın alma işlemi başlatılıyor...');
}
</script>

<style scoped>
</style>
