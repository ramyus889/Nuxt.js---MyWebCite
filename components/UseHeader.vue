<template>
  <v-app-bar :elevation="9">
    <template v-slot:prepend>
      <div class="flex sm:hidden">
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
      </div>
    </template>

    <v-app-bar-title> Frontend </v-app-bar-title>

    <template v-slot:append>
      <v-btn icon="mdi-magnify"></v-btn>
      <div class="hidden sm:block">
        <v-btn icon="mdi-home"></v-btn>
        <v-btn icon="mdi-api"></v-btn>
      </div>
    </template>
  </v-app-bar>
</template>
