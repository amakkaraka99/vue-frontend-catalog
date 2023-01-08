<script setup>
import axios from "axios";
import ProductDetail from "../components/ProductDetail.vue";
import { useRoute } from "vue-router";
import { ref, onMounted } from "vue";
const product = ref([]);
const route = useRoute();
const id = route.params.id;
const loading = ref(true);
const getProduct = async () => {
  const response = await axios.get(`https://fakestoreapi.com/products/${id}`);
  product.value = response.data;
  loading.value = false;
};
onMounted(getProduct);
</script>
<template>
  <div class="py-2 mt-20">
    <h1 class="font-semibold text-3xl md:text-5xl text-center text-blue-500">
      Detail Katalog
    </h1>
  </div>
  <span>
    <span v-if="loading">
      <div class="flex justify-center p-5">
        <div
          class="loader ease-linear rounded-full border-4 border-t-4 border-blue-900 h-12 w-12 mb-4"
        ></div>
      </div>
    </span>
    <span v-else>
      <ProductDetail :product="product" />
    </span>
  </span>
  <!-- {{ product }} -->
</template>
<style scoped>
img {
  max-width: 400px;
}
</style>
