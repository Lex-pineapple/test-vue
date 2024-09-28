<script setup lang="ts">
import { ref } from 'vue';
import BaseIcon from './icons/BaseIcon.vue';

const menuUnderlineWidth = ref('0');
const menuUnderlineOffset = ref('0');

const onMenuClick = (e: MouseEvent) => {
  menuUnderlineWidth.value = (e.target as HTMLDivElement).offsetWidth + 'px';
  menuUnderlineOffset.value = (e.target as HTMLDivElement).offsetLeft + 'px';
};
</script>

<template>
  <header class="header">
    <button class="burger-button">
      <div class="burger-button-container">
        <span class="burger-bar"></span>
        <span class="burger-bar"></span>
        <span class="burger-bar"></span>
      </div>
    </button>
    <BaseIcon type="owlIcon" viewBox="0 0 512 512" width="512" height="512" />
    <nav class="nav-menu" @click="onMenuClick">
      <div class="nav-menu__item">My Tasks</div>
      <div class="nav-menu__item">Team</div>
      <div class="nav-menu__item">Projects</div>
      <div class="nav-menu__underline"></div>
    </nav>
  </header>
</template>

<style scoped>
.header {
  padding: 0 20px;
  display: flex;
  align-items: center;
  height: 60px;
  border-bottom: 1px solid var(--color-border);
}

.svg-icon {
  height: 24px;
  width: 24px;
  margin: 0 20px;
}

.burger-button {
  padding: 10px;

  &:hover {
    background-color: var(--color-border);
    border-radius: 6px;
  }
}

.burger-button-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 14px;
}

.burger-bar {
  display: block;
  width: 20px;
  height: 2px;
  background-color: var(--color-dk-gray);
  /* background-color: red; */
}

.nav-menu {
  position: relative;
  display: flex;
  gap: 40px;
  color: var(--color-dk-gray);
  cursor: pointer;
  margin-left: 60px;

  &::before {
    content: '';
    display: block;
    position: absolute;
    top: 173%;
    height: 1px;
    background-color: var(--color-dk-gray);
    width: v-bind(menuUnderlineWidth);
    transform: translateX(v-bind(menuUnderlineOffset));
    transition:
      transform 0.5s,
      width 0.5s;
  }
}
</style>
