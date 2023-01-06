<script setup>
import Footer from "./components/Footer.vue";
import Navbra from "./components/Navbra.vue";
</script>
<template>
  <header>
    <Navbra />
  </header>
  <main>
    <RouterView />
  </main>
  <footer>
    <Footer />
  </footer>
</template>
