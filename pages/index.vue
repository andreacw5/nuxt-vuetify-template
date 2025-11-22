<template>
  <div>
    <v-row class="mb-6">
      <v-col cols="12">
        <ui-card
          title="Welcome to Nuxt 3 + Vuetify Template"
          subtitle="A modern, responsive starter template"
        >
          <p>
            This is a comprehensive template built with Nuxt 3 and Vuetify 3, featuring
            a responsive layout, reusable components, and modern design patterns.
          </p>
          <p>
            Explore the navigation to see all available pages and components.
          </p>

          <template #actions>
            <ui-button
              color="primary"
              prepend-icon="mdi-information"
              @click="navigateTo('/about')"
            >
              Learn More
            </ui-button>
            <ui-button
              variant="outlined"
              color="primary"
              prepend-icon="mdi-github"
              href="https://github.com"
              target="_blank"
            >
              View on GitHub
            </ui-button>
          </template>
        </ui-card>
      </v-col>
    </v-row>

    <v-row>
      <v-col v-for="feature in features" :key="feature.title" cols="12" md="4">
        <ui-card
          :title="feature.title"
          :subtitle="feature.subtitle"
          :text="feature.description"
        >
          <template #title>
            <v-icon :icon="feature.icon" class="mr-2" />
            {{ feature.title }}
          </template>
        </ui-card>
      </v-col>
    </v-row>
  </div>
</template>

<script setup lang="ts">
const features = [
  {
    icon: 'mdi-vuejs',
    title: 'Nuxt 3',
    subtitle: 'Latest Framework',
    description: 'Built with Nuxt 3, the intuitive Vue framework for building modern web applications.',
  },
  {
    icon: 'mdi-palette',
    title: 'Vuetify 3',
    subtitle: 'Material Design',
    description: 'Powered by Vuetify 3, providing beautiful Material Design components out of the box.',
  },
  {
    icon: 'mdi-responsive',
    title: 'Responsive',
    subtitle: 'Mobile First',
    description: 'Fully responsive design that works seamlessly across all devices and screen sizes.',
  },
  {
    icon: 'mdi-palette-swatch',
    title: 'Theming',
    subtitle: 'Dark & Light',
    description: 'Built-in theme switcher supporting both dark and light modes with custom colors.',
  },
  {
    icon: 'mdi-puzzle',
    title: 'Components',
    subtitle: 'Reusable',
    description: 'Pre-built reusable components for rapid application development.',
  },
  {
    icon: 'mdi-language-typescript',
    title: 'TypeScript',
    subtitle: 'Type Safe',
    description: 'Full TypeScript support for better developer experience and code quality.',
  },
];
</script>
