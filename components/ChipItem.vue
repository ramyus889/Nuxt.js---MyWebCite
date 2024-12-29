<script setup lang="ts">
defineProps({
  loading: Boolean,
  framework: String,
  imageFramework: String,
  linkFramework: String,
  library: String,
  imageLibrary: String,
  linkLibrary: String,
  UIFrameworkT: String,
  imageUIFrameworkT: String,
  linkUIFrameworkT: String,
  UIFrameworkP: String,
  imageUIFrameworkP: String,
  linkUIFrameworkP: String,
  Servis: String,
  imageServis: String,
  linkServis: String,
});
</script>

<template>
  <div class="flex flex-wrap gap-2 my-5 max-[400px]:place-content-center">
    <v-chip as="a" :href="linkFramework" target="_blank">
      <v-avatar start>
        <v-skeleton-loader
          v-if="loading"
          type="image"
          class="w-[30px] h-[30px]"
        ></v-skeleton-loader>
        <v-img v-else :src="imageFramework" />
      </v-avatar>
      {{ framework }}
    </v-chip>
    <v-chip as="a" :href="linkLibrary" target="_blank">
      <v-avatar start>
        <v-skeleton-loader
          v-if="loading"
          type="image"
          class="w-[30px] h-[30px]"
        ></v-skeleton-loader>
        <v-img v-else :src="imageLibrary" />
      </v-avatar>
      {{ library }}
    </v-chip>
    <v-chip as="a" :href="linkUIFrameworkT" target="_blank">
      <v-avatar start>
        <v-skeleton-loader
          v-if="loading"
          type="image"
          class="w-[30px] h-[30px]"
        ></v-skeleton-loader>
        <v-img v-else :src="imageUIFrameworkT" />
      </v-avatar>
      {{ UIFrameworkT }}
    </v-chip>
    <v-chip as="a" :href="linkUIFrameworkP" target="_blank">
      <v-avatar start>
        <v-skeleton-loader
          v-if="loading"
          type="image"
          class="w-[30px] h-[30px]"
        ></v-skeleton-loader>
        <v-img v-else :src="imageUIFrameworkP" />
      </v-avatar>
      {{ UIFrameworkP }}
    </v-chip>
    <v-chip as="a" :href="linkServis" target="_blank">
      <v-avatar start>
        <v-skeleton-loader
          v-if="loading"
          type="image"
          class="w-[30px] h-[30px]"
        ></v-skeleton-loader>
        <v-img v-else :src="imageServis" />
      </v-avatar>
      {{ Servis }}
    </v-chip>
  </div>
</template>
