<template>
  <div class="flex flex-col items-center gap-6">
    <div class="w-full max-w-7xl mx-auto bg-white rounded-lg shadow-md overflow-hidden p-8">
      <img
        :src="selectedImage"
        alt="Seçili Ürün Görseli"
        class="w-full h-[500px] object-contain transition-all duration-300 ease-in-out mx-auto"
      />
    </div>

    <!-- Thumbnail -->
    <div class="flex gap-4 overflow-x-auto no-scrollbar px-2">
      <div
        v-for="(img, index) in images"
        :key="index"
        @click="selectImage(img)"
        class="relative flex-shrink-0 w-20 h-20 rounded-lg overflow-hidden cursor-pointer group"
      >
        <img
          :src="img"
          :alt="'Thumbnail ' + (index + 1)"
          class="w-full h-full object-cover"
        />
        <div
          v-if="selectedImage === img"
          class="absolute bottom-0 left-0 w-full h-1 bg-blue-600 transition-all duration-300"
        ></div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

const images = ref<string[]>([]);
const selectedImage = ref('');

async function fetchImages() {
  try {
    const res = await fetch('https://dummyjson.com/products/9');
    const data = await res.json();
    images.value = data.images;
    selectedImage.value = data.images[0];
  } catch (err) {
    console.error('Görseller alınamadı:', err);
  }
}

onMounted(fetchImages);

function selectImage(img: string) {
  selectedImage.value = img;
}
</script>

<style scoped>
.no-scrollbar::-webkit-scrollbar {
  display: none;
}
.no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
</style>
