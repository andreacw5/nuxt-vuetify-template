<template>
  <v-app-bar :elevation="elevation" app>
    <template #prepend>
      <v-app-bar-nav-icon
        v-if="showNavIcon"
        @click="$emit('toggle-drawer')"
      />
    </template>

    <v-app-bar-title>
      <common-logo />
    </v-app-bar-title>

    <v-spacer />

    <div class="d-none d-sm-flex align-center">
      <v-btn
        v-for="item in navItems"
        :key="item.to"
        :to="item.to"
        :prepend-icon="item.icon"
        variant="text"
        rounded="lg"
      >
        {{ item.title }}
      </v-btn>
    </div>

    <template #append>
      <v-btn
        icon
        @click="toggleTheme"
      >
        <v-icon>{{ themeIcon }}</v-icon>
      </v-btn>
    </template>
  </v-app-bar>
</template>

<script setup lang="ts">
import { useTheme } from 'vuetify';

interface NavItem {
  title: string;
  to: string;
  icon?: string;
}

interface Props {
  elevation?: number;
  showNavIcon?: boolean;
  navItems?: NavItem[];
}

withDefaults(defineProps<Props>(), {
  elevation: 1,
  showNavIcon: true,
  navItems: () => [
    { title: 'Home', to: '/', icon: 'mdi-home' },
    { title: 'About', to: '/about', icon: 'mdi-information' },
  ],
});

defineEmits<{
  (e: 'toggle-drawer'): void;
}>();

const theme = useTheme();

const themeIcon = computed(() => {
  return theme.global.name.value === 'dark' ? 'mdi-weather-sunny' : 'mdi-weather-night';
});

const toggleTheme = () => {
  theme.global.name.value = theme.global.name.value === 'dark' ? 'light' : 'dark';
};
</script>
