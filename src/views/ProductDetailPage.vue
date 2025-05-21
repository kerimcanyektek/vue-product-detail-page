<template>
  <div class="min-h-screen bg-gray-100 py-10 px-4">
    <div class="max-w-7xl mx-auto bg-white rounded-lg shadow-md overflow-hidden p-8">
      <div v-if="loading" class="space-y-4 animate-pulse">
        <div class="h-96 bg-gray-300 rounded"></div>
        <div class="h-6 bg-gray-300 w-1/2 rounded"></div>
        <div class="h-4 bg-gray-300 w-1/3 rounded"></div>
      </div>

      <div v-else class="grid grid-cols-1 md:grid-cols-2 gap-16 items-start">
        <ProductGallery />
        <div class="space-y-8">
          <ProductInfo
            :title="'Dolce&Gabbana Devotion Edp Kadın Parfüm 100 ml'"
            :category="'Kadın Parfüm'"
            :price="5600"
          />
          <ProductDescription
            :longDescription="'Dolce&Gabbana Devotion Eau de Parfum, ikonik Kalp mührü ile sembolize edilen, baştan çıkarıcı duyusal bir yolculuk. Zarif kontrastların, parlak üst notaların ve şehvetli temel notaların birleşimi. TASARIM Kutsal kalp mührü Devotion Eau de Parfum şişesini süslüyor. Tüm şekilleri ve nüanslarıyla aşkın evrensel sembolü. ÜRÜN İÇERİĞİ: Şekerli Narenciye, Portakal Çiçeği, Vanilya.'"
          />
        </div>
      </div>
    </div>
    <SimilarProducts />
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import ProductGallery from '@/components/ProductGallery.vue';
import ProductInfo from '@/components/ProductInfo.vue';
import ProductDescription from '@/components/ProductDescription.vue';
import SimilarProducts from '@/components/SimilarProducts.vue';

const loading = ref(true);

async function fakeWait() {
  await new Promise((resolve) => setTimeout(resolve, 500));
  loading.value = false;
}

onMounted(() => {
  fakeWait();
});
</script>

<style scoped></style>
