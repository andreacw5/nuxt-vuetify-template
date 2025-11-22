<template>
  <v-card
    :elevation="elevation"
    :rounded="rounded"
    :variant="variant"
    :class="customClass"
  >
    <v-card-title v-if="title || $slots.title" class="card-title">
      <slot name="title">
        {{ title }}
      </slot>
    </v-card-title>

    <v-card-subtitle v-if="subtitle || $slots.subtitle" class="card-subtitle">
      <slot name="subtitle">
        {{ subtitle }}
      </slot>
    </v-card-subtitle>

    <v-card-text v-if="$slots.default || text" class="card-text">
      <slot>
        {{ text }}
      </slot>
    </v-card-text>

    <v-card-actions v-if="$slots.actions" class="card-actions">
      <slot name="actions" />
    </v-card-actions>
  </v-card>
</template>

<script setup lang="ts">
interface Props {
  title?: string;
  subtitle?: string;
  text?: string;
  elevation?: number | string;
  rounded?: boolean | string;
  variant?: 'flat' | 'text' | 'elevated' | 'tonal' | 'outlined' | 'plain';
  customClass?: string;
}

withDefaults(defineProps<Props>(), {
  title: undefined,
  subtitle: undefined,
  text: undefined,
  elevation: 2,
  rounded: 'lg',
  variant: 'elevated',
  customClass: '',
});
</script>

<style scoped>
.card-title {
  font-weight: 600;
}

.card-subtitle {
  opacity: 0.7;
}

.card-text {
  padding-top: 1rem;
}

.card-actions {
  padding: 1rem;
}
</style>
