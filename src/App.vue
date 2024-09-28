<script setup lang="ts">
import ContentComponent from './components/ContentComponent.vue'
import HeaderComponent from './components/HeaderComponent.vue'
import SidebarComponent from './components/SidebarComponent.vue'
</script>

<template>
  <div class="wrapper">
    <HeaderComponent />
    <main>
      <SidebarComponent />
      <ContentComponent />
    </main>
  </div>
</template>

<style scoped>
.wrapper {
  background-color: var(--color-white);
  width: 100%;
}
</style>
