<script setup>

</script>

<template>
  <UContainer>
    <main-nav />
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
