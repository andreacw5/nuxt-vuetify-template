<template>
  <v-navigation-drawer
    v-model="drawerModel"
    :rail="rail"
    app
    @update:rail="handleRailUpdate"
  >
    <template #prepend>
      <v-list-item
        :title="appTitle"
        :subtitle="appSubtitle"
        class="px-2"
      >
        <template #prepend>
          <common-logo :width="40" :height="40" />
        </template>

        <template #append>
          <v-btn
            icon
            variant="text"
            @click.stop="rail = !rail"
          >
            <v-icon>{{ rail ? 'mdi-chevron-right' : 'mdi-chevron-left' }}</v-icon>
          </v-btn>
        </template>
      </v-list-item>
    </template>

    <v-divider />

    <v-list density="compact" nav>
      <v-list-item
        v-for="item in navItems"
        :key="item.to"
        :to="item.to"
        :prepend-icon="item.icon"
        :title="item.title"
        rounded="lg"
      />
    </v-list>
  </v-navigation-drawer>
</template>

<script setup lang="ts">
interface NavItem {
  title: string;
  to: string;
  icon?: string;
}

interface Props {
  modelValue?: boolean;
  appTitle?: string;
  appSubtitle?: string;
  navItems?: NavItem[];
}

const props = withDefaults(defineProps<Props>(), {
  modelValue: false,
  appTitle: 'Nuxt + Vuetify',
  appSubtitle: 'Template',
  navItems: () => [
    { title: 'Home', to: '/', icon: 'mdi-home' },
    { title: 'About', to: '/about', icon: 'mdi-information' },
  ],
});

const emit = defineEmits<{
  (e: 'update:modelValue', value: boolean): void;
}>();

const rail = ref(false);

const drawerModel = computed({
  get: () => props.modelValue,
  set: (value) => emit('update:modelValue', value),
});

const handleRailUpdate = (value: boolean) => {
  rail.value = value;
};
</script>
