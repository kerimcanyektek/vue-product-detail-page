<template>
  <div class="space-y-6">
    <!-- Ürün Başlığı -->
    <h1 class="text-3xl font-bold text-gray-900">
      {{ title }}
    </h1>

    
    <!-- Ürün Puanı -->
    <div class="flex items-center space-x-1 text-yellow-400 text-xl">
      <span>★★★★☆</span>
      <span class="text-sm text-gray-500">(4.5)</span>
    </div>

    <!-- Ürün Kategorisi -->
    <p class="text-gray-600 leading-relaxed">
      {{ category }}
    </p>

    <!-- Ürün Fiyatı -->
    <div class="flex items-center space-x-2">
      <span class="text-3xl font-extrabold text-green-600">
        {{ price }}₺
      </span>
    </div>

    <!-- Butonlar -->
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

const emit = defineEmits<{
  (e: 'add-to-cart'): void;
  (e: 'buy-now'): void;
}>();

function addToCart() {
  emit('add-to-cart');
}

function buyNow() {
  emit('buy-now');
}
</script>
