<template>
  <div class="max-w-7xl mx-auto bg-white rounded-lg shadow-md p-8 mt-12">
    <h2 class="text-2xl font-semibold mb-6">Benzer Ürünler</h2>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
      <div
        v-for="item in products"
        :key="item.id"
        class="border rounded-lg overflow-hidden shadow hover:shadow-lg transition"
      >
        <img :src="item.thumbnail" alt="" class="w-full h-48 object-cover" />
        <div class="p-4">
          <h3 class="font-semibold text-lg">{{ item.title }}</h3>
          <p class="text-green-600 font-bold mt-2">{{ item.price }}₺</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

const products = ref<any[]>([]);

async function fetchSimilarProducts() {
  try {
    const res = await fetch('https://dummyjson.com/products/category/fragrances?limit=4');
    const data = await res.json();
    products.value = data.products;
  } catch (err) {
    console.error('Benzer ürünler alınamadı:', err);
  }
}

onMounted(() => {
  fetchSimilarProducts();
});
</script>
