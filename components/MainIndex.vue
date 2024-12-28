<template>
  <div class="flex flex-col gap-20">
    <div v-for="item in items1" :key="item.id" class="">
      <div
        class="flex lg:flex-row flex-col gap-10 bg-[#212121] rounded-xl py-5 px-5"
      >
        <div class="flex place-content-center">
          <v-skeleton-loader
            v-if="item.loading"
            type="image"
            class="w-[600px] v-skeleton-loader"
          ></v-skeleton-loader>
          <img v-else :src="item.image" class="rounded-xl" width="600" alt="" />
        </div>
        <div class="mt-5">
          <div class="text-2xl">{{ item.title }}</div>
          <div class="">
            <a
              :href="item.link"
              target="_blank"
              class="hover:text-[#3b82f6] transition-colors"
              >{{ item.description }}</a
            >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { items1 as originalItems } from "../Items";

const items1 = ref(originalItems.map((item) => ({ ...item, loading: true })));

onMounted(async () => {
  for (const item of items1.value) {
    try {
      const response = await fetch(item.image);
      if (response.ok) {
        item.loading = false;
      }
    } catch (error) {
      console.error("Error loading image:", error);
    }
  }
});
</script>

<style scoped>
.v-skeleton-loader {
  border-radius: 16px;
  height: 422px;
}
</style>
