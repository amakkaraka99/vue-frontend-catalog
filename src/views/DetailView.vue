<script setup>
import axios from "axios";
import ProductDetail from "../components/ProductDetail.vue";
import { useRoute } from "vue-router";
import { ref, onMounted } from "vue";
const product = ref([]);
const route = useRoute();
const id = route.params.id;
const getProduct = async () => {
  const response = await axios.get(`https://fakestoreapi.com/products/${id}`);
  product.value = response.data;
};
onMounted(getProduct);
</script>
<template>
  <div class="py-2 mt-4">
    <h1 class="font-semibold text-3xl md:text-5xl text-center text-blue-500">
      Detail Katalog
    </h1>
  </div>
  <ProductDetail :product="product" />
  <!-- {{ product }} -->
</template>
<style scoped>
img {
  max-width: 400px;
}
</style>
