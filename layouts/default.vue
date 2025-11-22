<template>
  <v-app>
    <!--[if lte IE 9]>
    <p class="browserupgrade">
    You are using an <strong>outdated</strong> browser. Please
    <a href="https://browsehappy.com/">upgrade your browser</a> to improve
    your experience and security.
    </p>
    <![endif]-->

    <common-app-bar @toggle-drawer="drawer = !drawer" />

    <common-navigation-drawer v-model="drawer" />

    <v-main>
      <v-container fluid>
        <slot />
      </v-container>
    </v-main>

    <common-footer />
  </v-app>
</template>

<script setup lang="ts">
const drawer = ref(false);
</script>
