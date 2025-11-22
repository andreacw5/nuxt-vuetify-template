<template>
  <div class="logo-container">
    <nuxt-link to="/" class="logo-link">
      <v-img
        v-if="src"
        :src="src"
        :alt="alt"
        :width="width"
        :height="height"
        contain
      />
      <span v-else class="logo-text">
        {{ text }}
      </span>
    </nuxt-link>
  </div>
</template>

<script setup lang="ts">
interface Props {
  src?: string;
  alt?: string;
  text?: string;
  width?: number | string;
  height?: number | string;
}

withDefaults(defineProps<Props>(), {
  src: '',
  alt: 'Logo',
  text: 'Nuxt + Vuetify',
  width: 180,
  height: 40,
});
</script>

<style scoped>
.logo-container {
  display: flex;
  align-items: center;
}

.logo-link {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: inherit;
}

.logo-text {
  font-size: 1.5rem;
  font-weight: 700;
  color: rgb(var(--v-theme-primary));
}
</style>
