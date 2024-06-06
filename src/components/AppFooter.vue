<template>
  <v-footer height="40" app>
    <a
      v-for="item in items"
      :key="item.title"
      :href="item.href"
      :title="item.title"
      class="d-inline-block mx-2 social-link"
      rel="noopener noreferrer"
      target="_blank"
    >
      <v-icon
        :icon="item.icon"
        :size="item.icon === '$vuetify' ? 24 : 16"
      />
    </a>

    <div
      class="text-caption text-disabled"
      style="position: absolute; right: 16px;"
    >
      &copy; 2023-{{ (new Date()).getFullYear() }} <span class="d-none d-sm-inline-block">Daniel Foulkes - NARDHC</span>
      —
      <a
        class="text-decoration-none on-surface"
        href=""
        rel="noopener noreferrer"
        target="_blank"
      >
        MIT License
      </a>
    </div>
  </v-footer>
</template>

<script setup>
  const items = [
    {
      title: 'NARDHC Documentation',
      icon: 'mdi-shield-star-outline',
      href: 'https://nardhc.org/',
    },
    {
      title: 'NARDHC LinkedIn',
      icon: 'mdi-linkedin',
      href: 'https://x.com/vuetifyjs',
    },
    {
      title: 'NARDHC GitHub',
      icon: `mdi-github`,
      href: 'https://github.com/dfoulkesjcu/arf-register-fsh',
    },
  ]
</script>

<style scoped lang="sass">
  .social-link :deep(.v-icon)
    color: rgba(var(--v-theme-on-background), var(--v-disabled-opacity))
    text-decoration: none
    transition: .2s ease-in-out

    &:hover
      color: rgba(25, 118, 210, 1)
</style>
