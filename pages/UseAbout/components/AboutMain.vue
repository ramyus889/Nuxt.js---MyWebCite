<template>
  <div class="flex flex-col gap-20">
    <div v-for="item in items1" :key="item.id" class="">
      <div
        class="flex lg:flex-row flex-col sm:gap-10 gap-7 bg-[#212121] rounded-xl py-5 px-3"
      >
        <div class="flex place-content-center">
          <v-skeleton-loader
            v-if="item.loading"
            type="image"
            class="w-[600px] v-skeleton-loader"
          ></v-skeleton-loader>
          <img v-else :src="item.image" class="rounded-xl" width="600" alt="" />
        </div>
        <div class="sm:mt-3">
          <div class="text-2xl">{{ item.title }}</div>
          <div class="">
            <a
              :href="item.link"
              target="_blank"
              class="text-[#3b82f6] hover:text-[#2b60b6] transition-colors"
              >{{ item.description }}</a
            >
          </div>
          <ChipItem
            :loading="item.loading"
            :framework="item.framework"
            :linkFramework="item.linkFramework"
            :imageFramework="item.imageFramework"
            :library="item.library"
            :linkLibrary="item.linkLibrary"
            :imageLibrary="item.imageLibrary"
            :UIFrameworkT="item.UIFrameworkT"
            :linkUIFrameworkT="item.linkUIFrameworkT"
            :imageUIFrameworkT="item.imageUIFrameworkT"
            :UIFrameworkP="item.UIFrameworkP"
            :linkUIFrameworkP="item.linkUIFrameworkP"
            :imageUIFrameworkP="item.imageUIFrameworkP"
            :Servis="item.Servis"
            :linkServis="item.linkServis"
            :imageServis="item.imageServis"
          />
          <div class="mt-5 max-w-[600px]">
            {{ item.descriptionChip }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { items1 as originalItems } from "../../../Items";

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
.v-skeleton-loader:deep(.v-skeleton-loader__image) {
  border-radius: 16px;
  height: 422px;
}
@media screen and (max-width: 500px) {
  .v-skeleton-loader:deep(.v-skeleton-loader__image) {
    height: 250px;
  }
}
</style>
