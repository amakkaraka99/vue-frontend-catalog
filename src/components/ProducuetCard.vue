<script setup>
const { product } = defineProps(["product"]);
</script>
<template>
  <div
    class="p-4 rounded-md bg-white shadow-sm hover:shadow-xl h-full text-center justify-center"
  >
    <img
      :src="product.image"
      alt="product"
      class="thumb hover:scale-125 transition duration-500 ease-in-out transform hover:rotate-3"
    />
    <p class="font-bold text-gray-500 m-4">
      {{ product.title }}
    </p>
    <p>price: $ {{ product.price }}</p>
    <RouterLink :to="'/detail/' + product.id"
      ><p
        class="bg-[#1232b4] text-white py-2 hover:bg-yellow-500 rounded-md text-sm my-4"
      >
        View Details
      </p>
    </RouterLink>
  </div>
</template>
<style scoped>
.thumb {
  max-height: 120px;
  max-width: 70%;
  margin: 0 auto;
}
</style>
