<template>
  <div class="mt-8 space-y-4">
    <h2 class="text-2xl font-bold text-gray-800">
      Ürün Açıklaması
    </h2>
    <p class="text-gray-600 leading-relaxed">
      {{ longDescription }}
    </p>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  longDescription: string
}>();
</script>
