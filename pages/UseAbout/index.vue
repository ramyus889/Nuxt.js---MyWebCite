<script setup lang="ts">
import AboutMain from "./components/AboutMain.vue";
useHead({
  title: "MyWebSite - Сайты",
  link: [{ rel: "icon", type: "image/x-icon", href: "/img/Code/frontend.jpg" }],
});
</script>
<template>
  <div
    class="my-[150px] min-[2300px]:mx-[500px] min-[2100px]:mx-[400px] min-[1900px]:mx-[300px] min-[1600px]:mx-[150px] max-[1600px]:mx-5"
  >
    <AboutMain />
  </div>
</template>
