<script setup>
import axios from "axios";
import ProductCard from "../components/ProducuetCard.vue";
import { ref, onMounted, computed } from "vue";
import HeroSection from "../components/HeroSection.vue";
const products = ref([]);
const loading = ref(true);
const getProducts = async () => {
  const response = await axios.get("https://fakestoreapi.com/products");
  products.value = response.data;
  loading.value = false;
};
onMounted(getProducts);
const search = ref("");
const filteredProducts = computed(() => {
  return products.value.filter((p) => {
    return p.title.toLowerCase().includes(search.value.toLowerCase());
  });
});
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
      <span>
        <span v-if="loading">
          <div class="flex justify-center p-5">
            <div
              class="loader ease-linear rounded-full border-4 border-t-4 border-rose-900 h-12 w-12 mb-4"
            ></div>
          </div>
        </span>
        <span v-else>
          <div
            class="grid sm:grid-cols-2 :grid-cols-2 md:grid-cols-3 xl:grid-cols-4 gap-6 md:gap-5"
          >
            <div
              v-for="p in filteredProducts"
              :key="p.id"
              class="mb-4 justify-center"
            >
              <ProductCard :product="p" />
            </div>
          </div>
        </span>
      </span>
    </div>
  </section>
</template>
