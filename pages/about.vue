<template>
  <div>
    <v-row>
      <v-col cols="12">
        <ui-card
          title="About This Template"
          subtitle="Learn more about the Nuxt 3 + Vuetify Template"
        >
          <p>
            This template is designed to help you kickstart your next web application
            project with a solid foundation. It combines the power of Nuxt 3's server-side
            rendering capabilities with Vuetify 3's beautiful Material Design components.
          </p>
        </ui-card>
      </v-col>
    </v-row>

    <v-row class="mt-4">
      <v-col cols="12" md="6">
        <ui-card title="Features">
          <v-list>
            <v-list-item
              v-for="feature in features"
              :key="feature"
              :prepend-icon="'mdi-check-circle'"
            >
              <v-list-item-title>{{ feature }}</v-list-item-title>
            </v-list-item>
          </v-list>
        </ui-card>
      </v-col>

      <v-col cols="12" md="6">
        <ui-card title="Technologies">
          <v-list>
            <v-list-item
              v-for="tech in technologies"
              :key="tech.name"
              :prepend-icon="tech.icon"
            >
              <v-list-item-title>{{ tech.name }}</v-list-item-title>
              <v-list-item-subtitle>{{ tech.description }}</v-list-item-subtitle>
            </v-list-item>
          </v-list>
        </ui-card>
      </v-col>
    </v-row>

    <v-row class="mt-4">
      <v-col cols="12">
        <ui-card title="Getting Started">
          <p>To start using this template, follow these simple steps:</p>
          <ol>
            <li>Clone the repository to your local machine</li>
            <li>Install dependencies with <code>yarn install</code></li>
            <li>Start the development server with <code>yarn dev</code></li>
            <li>Begin building your application!</li>
          </ol>

          <template #actions>
            <ui-button
              color="primary"
              prepend-icon="mdi-github"
              href="https://github.com"
              target="_blank"
            >
              View Documentation
            </ui-button>
            <ui-button
              variant="outlined"
              prepend-icon="mdi-home"
              @click="navigateTo('/')"
            >
              Back to Home
            </ui-button>
          </template>
        </ui-card>
      </v-col>
    </v-row>
  </div>
</template>

<script setup lang="ts">
const features = [
  'Server-side rendering (SSR)',
  'Responsive layout with AppBar, Navigation Drawer, and Footer',
  'Reusable UI components',
  'Dark and Light theme support',
  'TypeScript integration',
  'i18n internationalization support',
  'PWA ready with workbox',
  'Image optimization',
];

const technologies = [
  {
    name: 'Nuxt 3',
    description: 'The Intuitive Vue Framework',
    icon: 'mdi-vuejs',
  },
  {
    name: 'Vuetify 3',
    description: 'Material Design Component Framework',
    icon: 'mdi-palette',
  },
  {
    name: 'TypeScript',
    description: 'Typed JavaScript',
    icon: 'mdi-language-typescript',
  },
  {
    name: 'Pinia',
    description: 'State Management',
    icon: 'mdi-database',
  },
  {
    name: 'Vite',
    description: 'Next Generation Frontend Tooling',
    icon: 'mdi-lightning-bolt',
  },
];
</script>

<style scoped>
code {
  background-color: rgba(var(--v-theme-surface-variant), 0.2);
  padding: 0.2rem 0.4rem;
  border-radius: 4px;
  font-family: monospace;
}

ol {
  padding-left: 1.5rem;
  margin-top: 1rem;
}

ol li {
  margin-bottom: 0.5rem;
}
</style>
