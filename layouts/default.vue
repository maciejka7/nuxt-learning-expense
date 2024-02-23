<script setup>
const links = [
  [
    {
      label: 'Profile',
      avatar: {
        src: 'https://avatars.githubusercontent.com/u/18124391?v=4',
      },
    },
    {
      label: 'Home',
      icon: 'i-heroicons-home',
      to: '/',
    },
    {
      label: 'Stats',
      icon: 'i-heroicons-chart-bar',
      to: `/stats`,
    },
    {
      label: 'About',
      icon: 'i-heroicons-information-circle',
      to: '/about',
    },
  ],
];
</script>

<template>
  <UContainer>
    <div class="flex"> 
      <u-horizontal-navigation :links="links" class="border-b border-gray-200 dark:border-gray-800" />
      <client-only> 
      <color-mode-switcher />
      </client-only>
    </div>
    <div class="p-2">
      <slot />
    </div>
    <footer>
      <UContainer class="text-center"> made with ❤ and
        <UIcon name="logos:nuxt-icon" dynamic />
        <UIcon name="logos:vue" dynamic />
      </UContainer>
    </footer>
  </UContainer>
</template>
