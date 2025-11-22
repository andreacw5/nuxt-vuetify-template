<template>
  <nuxt-layout name="blank">
    <div class="error-page">
      <v-container>
        <v-row align="center" justify="center" style="min-height: 100vh;">
          <v-col cols="12" md="6">
            <ui-card class="text-center">
              <div class="error-icon">
                <v-icon :icon="errorIcon" size="120" :color="errorColor" />
              </div>

              <v-card-title class="text-h3 mb-4">
                {{ errorTitle }}
              </v-card-title>

              <v-card-subtitle class="text-h5 mb-4">
                {{ error?.statusCode || 'Error' }}
              </v-card-subtitle>

              <v-card-text>
                <p class="text-h6 mb-4">
                  {{ errorMessage }}
                </p>
                <p class="text-body-1 text-medium-emphasis">
                  {{ errorDescription }}
                </p>
              </v-card-text>

              <template #actions>
                <div class="d-flex justify-center ga-2 flex-wrap">
                  <ui-button
                    color="primary"
                    prepend-icon="mdi-home"
                    @click="handleError"
                  >
                    Back to Home
                  </ui-button>
                  <ui-button
                    variant="outlined"
                    prepend-icon="mdi-arrow-left"
                    @click="goBack"
                  >
                    Go Back
                  </ui-button>
                </div>
              </template>
            </ui-card>
          </v-col>
        </v-row>
      </v-container>
    </div>
  </nuxt-layout>
</template>

<script setup lang="ts">
interface Props {
  error?: {
    statusCode?: number;
    statusMessage?: string;
    message?: string;
  };
}

const props = defineProps<Props>();

const errorTitle = computed(() => {
  if (props.error?.statusCode === 404) {
    return 'Page Not Found';
  } else if (props.error?.statusCode === 500) {
    return 'Internal Server Error';
  } else if (props.error?.statusCode === 403) {
    return 'Access Forbidden';
  }
  return 'Oops! Something went wrong';
});

const errorMessage = computed(() => {
  if (props.error?.statusCode === 404) {
    return 'The page you are looking for does not exist.';
  } else if (props.error?.statusCode === 500) {
    return 'We encountered an unexpected error.';
  } else if (props.error?.statusCode === 403) {
    return 'You do not have permission to access this page.';
  }
  return props.error?.message || props.error?.statusMessage || 'An unexpected error occurred.';
});

const errorDescription = computed(() => {
  if (props.error?.statusCode === 404) {
    return 'The page might have been moved, deleted, or the URL might be incorrect.';
  } else if (props.error?.statusCode === 500) {
    return 'Our team has been notified and is working on fixing the issue.';
  }
  return 'Please try again later or return to the homepage.';
});

const errorIcon = computed(() => {
  if (props.error?.statusCode === 404) {
    return 'mdi-file-question';
  } else if (props.error?.statusCode === 500) {
    return 'mdi-alert-circle';
  } else if (props.error?.statusCode === 403) {
    return 'mdi-lock';
  }
  return 'mdi-alert';
});

const errorColor = computed(() => {
  if (props.error?.statusCode === 404) {
    return 'warning';
  } else if (props.error?.statusCode === 500) {
    return 'error';
  } else if (props.error?.statusCode === 403) {
    return 'info';
  }
  return 'error';
});

const handleError = () => {
  clearError({ redirect: '/' });
};

const goBack = () => {
  if (process.client) {
    if (window.history.length > 1) {
      window.history.back();
    } else {
      navigateTo('/');
    }
  } else {
    navigateTo('/');
  }
};
</script>

<style scoped>
.error-page {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.error-icon {
  margin: 2rem 0;
}
</style>
