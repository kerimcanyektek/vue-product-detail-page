<template>
  <div class="flex flex-col min-h-screen">
    <!-- Header -->
    <Header />

    <!-- Main Content -->
    <main class="flex-1 mt-16">
      <ProductDetailPage />
    </main>

    <!-- Footer -->
    <Footer />
  </div>
</template>

<script setup lang="ts">
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import ProductDetailPage from './views/ProductDetailPage.vue';
</script>
