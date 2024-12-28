<script setup lang="ts">
import { useWindowSize } from "@vueuse/core";
import { ref } from "vue";

const show = ref(false);
const { width } = useWindowSize();
const isScreenLarge = ref(width.value >= 640);
const isScreenLargeDescktop = ref(width.value <= 640);

watch(width, (newWidth) => {
  isScreenLarge.value = newWidth >= 640;
  isScreenLargeDescktop.value = newWidth <= 640;
});
</script>

<template>
  <div class="fixed top-0 left-0 right-0 z-50">
    <div
      :class="show ? 'px-3 py-3' : 'p-4'"
      class="bg-[#212121] shadow-md flex flex-col max-[640px]:transition-all max-[640px]:duration-500"
    >
      <div class="flex items-center justify-between">
        <div class="flex sm:hidden">
          <v-btn icon="mdi-menu" elevation="0"></v-btn>
        </div>

        <div class="text-lg font-semibold">Frontend</div>

        <v-text-field
          v-show="isScreenLarge"
          v-if="show"
          label="Search"
          prepend-inner-icon="mdi-magnify"
          max-width="800px"
          hide-details
          class="px-10 motion-preset-blur-down-lg motion-safe:duration-500"
        ></v-text-field>

        <div class="flex items-center gap-5">
          <v-btn icon="mdi-magnify" elevation="0" @click="show = !show"></v-btn>
          <div class="items-center hidden gap-5 sm:flex">
            <v-btn icon="mdi-home" elevation="0" as="nuxt-link" to="/"></v-btn>
            <v-btn
              icon="mdi-api"
              as="nuxt-link"
              to="/useAbout"
              elevation="0"
            ></v-btn>
          </div>
        </div>
      </div>
      <div class="">
        <v-text-field
          v-show="isScreenLargeDescktop"
          v-if="show"
          label="Search"
          prepend-inner-icon="mdi-magnify"
          max-width="full"
          hide-details
          class="mt-5 mb-2 motion-preset-blur-down-lg motion-safe:duration-500"
        ></v-text-field>
      </div>
    </div>
  </div>
</template>
