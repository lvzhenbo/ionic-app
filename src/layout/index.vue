<template>
  <div>
    <MenuLayout />
    <PageLayout />
  </div>
</template>

<script setup lang="ts">
  import MenuLayout from './menu.vue';
  import PageLayout from './page.vue';
  defineOptions({
    name: 'LayoutIndex',
  });
</script>

<style scoped></style>
