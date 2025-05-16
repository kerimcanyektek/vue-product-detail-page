<template>
  <div class="space-y-6">
    <!-- Product Title -->
    <h1 class="text-3xl font-bold text-gray-900">
      {{ title }}
    </h1>

    <!-- Product Category -->
    <p class="text-gray-500 text-sm">
      {{ description }}
    </p>

    <!-- Price -->
    <div class="flex items-center space-x-2">
      <span class="text-3xl font-extrabold text-green-600">
        {{ price.toLocaleString('tr-TR') }} TL
      </span>
    </div>

    <!-- Add To Cart -->
    <button
      @click="addToCart"
      class="w-full md:w-auto px-6 py-3 bg-blue-600 hover:bg-blue-700 text-white font-semibold rounded-lg transition duration-300"
    >
      Sepete Ekle
    </button>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  title: string;
  description: string;
  price: number;
}>();

const emit = defineEmits<{
  (e: 'add-to-cart'): void;
}>();

function addToCart() {
  emit('add-to-cart');
}
</script>

<style scoped>
</style>
