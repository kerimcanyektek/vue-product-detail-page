<template>
  <div class="min-h-screen bg-gray-100 py-10 px-4">
    <div class="max-w-7xl mx-auto bg-white rounded-lg shadow-md overflow-hidden p-8">
      <div v-if="loading" class="space-y-4 animate-pulse">
        <!-- Loading Skeleton -->
        <div class="h-96 bg-gray-300 rounded"></div>
        <div class="h-6 bg-gray-300 w-1/2 rounded"></div>
        <div class="h-4 bg-gray-300 w-1/3 rounded"></div>
      </div>

      <div v-else class="grid grid-cols-1 md:grid-cols-2 gap-16 items-start">
        <!-- Product Gallery -->
        <ProductGallery :images="productImages" />

        <!-- Product Info -->
        <div class="space-y-8">
          <ProductInfo
            :title="customTitle"
            :category="customCategory"
            :price="customPrice"
            @add-to-cart="showToast"
          />
          <ProductDescription :longDescription="customDescription" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import ProductGallery from '@/components/ProductGallery.vue';
import ProductInfo from '@/components/ProductInfo.vue';
import ProductDescription from '@/components/ProductDescription.vue';

const loading = ref(true);
const productImages = ref<string[]>([]);


const customTitle = 'Dolce&Gabbana Devotion Edp Kadın Parfüm 100 ml';
const customPrice = 5600;
const customCategory = 'Kadın Parfüm';
const customDescription = 'Dolce&Gabbana Devotion Eau de Parfum, ikonik Kalp mührü ile sembolize edilen, baştan çıkarıcı duyusal bir yolculuk. Zarif kontrastların, parlak üst notaların ve şehvetli temel notaların birleşimi. TASARIM Kutsal kalp mührü Devotion Eau de Parfum şişesini süslüyor. Tüm şekilleri ve nüanslarıyla aşkın evrensel sembolü ÜRÜN İÇERİĞİ Şekerli Narenciye: Baştan çıkarıcı, gurme Portakal Çiçeği: Taze ve narin Vanilya: Tatlı ve şehvetli';

async function fetchProductImages() {
  try {
    const res = await fetch('https://dummyjson.com/products/9');
    const data = await res.json();
    productImages.value = data.images;
  } catch (err) {
    console.error('Hata:', err);
  } finally {
    loading.value = false;
  }
}

function showToast() {
  alert('🎉 Ürün sepete eklendi!');
}

onMounted(() => {
  fetchProductImages();
});
</script>

<style scoped>
</style>
