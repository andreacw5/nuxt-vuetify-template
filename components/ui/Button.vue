<template>
  <v-btn
    :variant="variant"
    :color="color"
    :size="size"
    :rounded="rounded"
    :prepend-icon="prependIcon"
    :append-icon="appendIcon"
    :loading="loading"
    :disabled="disabled"
    :block="block"
    :class="customClass"
    @click="handleClick"
  >
    <slot />
  </v-btn>
</template>

<script setup lang="ts">
interface Props {
  variant?: 'flat' | 'text' | 'elevated' | 'tonal' | 'outlined' | 'plain';
  color?: string;
  size?: 'x-small' | 'small' | 'default' | 'large' | 'x-large';
  rounded?: boolean | string;
  prependIcon?: string;
  appendIcon?: string;
  loading?: boolean;
  disabled?: boolean;
  block?: boolean;
  customClass?: string;
}

withDefaults(defineProps<Props>(), {
  variant: 'flat',
  color: 'primary',
  size: 'default',
  rounded: 'lg',
  prependIcon: undefined,
  appendIcon: undefined,
  loading: false,
  disabled: false,
  block: false,
  customClass: '',
});

const emit = defineEmits<{
  (e: 'click', event: MouseEvent): void;
}>();

const handleClick = (event: MouseEvent) => {
  emit('click', event);
};
</script>
