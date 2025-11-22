<template>
  <v-footer app class="footer">
    <v-container>
      <v-row align="center" justify="center">
        <v-col cols="12" md="4" class="text-center text-md-left">
          <common-logo :width="150" :height="35" />
          <p class="mt-2 text-caption">{{ description }}</p>
        </v-col>

        <v-col cols="12" md="4" class="text-center">
          <div class="footer-links">
            <nuxt-link
              v-for="link in footerLinks"
              :key="link.to"
              :to="link.to"
              class="footer-link"
            >
              {{ link.title }}
            </nuxt-link>
          </div>
        </v-col>

        <v-col cols="12" md="4" class="text-center text-md-right">
          <div class="social-links">
            <v-btn
              v-for="social in socialLinks"
              :key="social.name"
              :icon="social.icon"
              :href="social.url"
              target="_blank"
              variant="text"
              size="small"
            />
          </div>
        </v-col>
      </v-row>

      <v-divider class="my-4" />

      <v-row>
        <v-col cols="12" class="text-center">
          <p class="text-caption mb-0">
            © {{ currentYear }} {{ copyrightText }}
          </p>
        </v-col>
      </v-row>
    </v-container>
  </v-footer>
</template>

<script setup lang="ts">
interface FooterLink {
  title: string;
  to: string;
}

interface SocialLink {
  name: string;
  icon: string;
  url: string;
}

interface Props {
  description?: string;
  copyrightText?: string;
  footerLinks?: FooterLink[];
  socialLinks?: SocialLink[];
}

withDefaults(defineProps<Props>(), {
  description: 'A modern Nuxt 3 + Vuetify template for building web applications.',
  copyrightText: 'Nuxt + Vuetify Template. All rights reserved.',
  footerLinks: () => [
    { title: 'Home', to: '/' },
    { title: 'About', to: '/about' },
    { title: 'Contact', to: '/contact' },
  ],
  socialLinks: () => [
    { name: 'GitHub', icon: 'mdi-github', url: 'https://github.com' },
    { name: 'Twitter', icon: 'mdi-twitter', url: 'https://twitter.com' },
    { name: 'LinkedIn', icon: 'mdi-linkedin', url: 'https://linkedin.com' },
  ],
});

const currentYear = computed(() => new Date().getFullYear());
</script>

<style scoped>
.footer {
  border-top: 1px solid rgba(var(--v-border-color), var(--v-border-opacity));
}

.footer-links {
  display: flex;
  gap: 1.5rem;
  justify-content: center;
  flex-wrap: wrap;
}

.footer-link {
  text-decoration: none;
  color: inherit;
  font-size: 0.875rem;
  transition: opacity 0.2s;
}

.footer-link:hover {
  opacity: 0.7;
}

.social-links {
  display: flex;
  gap: 0.5rem;
  justify-content: center;
}

@media (min-width: 960px) {
  .social-links {
    justify-content: flex-end;
  }
}
</style>
