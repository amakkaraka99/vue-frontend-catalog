<template>
  <nav
    class="flex flex-wrap fixed top-0 z-50 items-center justify-between w-full py-0 md:py-0 px-4 text-lg text-white bg-[#002447]"
  >
    <div>
      <a href="#">
        <img src="../assets/logo.png" alt="" />
      </a>
    </div>

    <svg
      @click="menuToggle"
      xmlns="http://www.w3.org/2000/svg"
      id="menu-button"
      class="h-6 w-6 cursor-pointer md:hidden block"
      fill="none"
      viewBox="0 0 24 24"
      stroke="currentColor"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        stroke-width="2"
        d="M4 6h16M4 12h16M4 18h16"
      />
    </svg>

    <div :class="navtoggle" id="menu">
      <ul
        class="text-2xl font-semibold pt-4 text-white md:flex md:justify-between md:pt-0"
      >
        <li>
          <RouterLink to="/">
            <a class="md:p-4 py-2 block hover:text-yellow-400" href="#">Home</a>
          </RouterLink>
        </li>
        <li>
          <RouterLink to="/about">
            <a class="md:p-4 py-2 block hover:text-yellow-400" href="#"
              >About</a
            >
          </RouterLink>
        </li>

        <li>
          <!-- <a
            class="md:p-4 py-2 block hover:text-purple-400 text-purple-500"
            href="#"
            >Sign Up</a
          > -->
        </li>
      </ul>
    </div>
    <div class="bg-yellow-300 p-0.5 mx-auto mt-4 md:mt-0 w-full"></div>
  </nav>
</template>
<script setup>
import { ref } from "vue";
const navtoggle = ref("");

const navHidden = ref("hidden w-full md:flex md:items-center md:w-auto");
const navVisible = ref(" w-full md:flex md:items-center md:w-auto");
const visible = ref(true);
const menuToggle = () => {
  if (visible.value) {
    navtoggle.value = navVisible.value;
    visible.value = false;
  } else {
    navtoggle.value = navHidden.value;
    visible.value = true;
  }
};
</script>
<style scoped>
img {
  max-height: 50px;
}
</style>
