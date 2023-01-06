<script setup>
import axios from "axios";
import ProductCard from "../components/ProducuetCard.vue";
import { ref, onMounted } from "vue";
import HeroSection from "../components/HeroSection.vue";
const products = ref([]);
const getProducts = async () => {
  const response = await axios.get("https://fakestoreapi.com/products");
  products.value = response.data;
};
onMounted(getProducts);
const search = ref("");
</script>

<template>
  <HeroSection />
  <section id="shop">
    <div class="container px-6">
      <h1 class="text-4xl text-center text-blue-700 font-semibold my-8">
        Katalog Produk SMAN 9 Luwu Utara
      </h1>
      <div class="flex">
        <input
          type="search"
          class="md:w-1/2 w-full hover:bg-yellow-200 mb-8 mx-auto p-3 rounded-md"
          placeholder="Cari Produk"
          v-model="search"
        />
      </div>
      <div
        class="grid sm:grid-cols-2 justify-between :grid-cols-2 md:grid-cols-3 xl:grid-cols-4 gap-6 md:gap-5"
      >
        <div v-for="p in products" :key="p.id" class="mb-4">
          <ProductCard :product="p" />
        </div>
      </div>
    </div>
  </section>
</template>
