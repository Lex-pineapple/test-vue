<template>
  <svg
    :viewBox="viewBox"
    :width="width"
    :height="height"
    xmlns="http://www.w3.org/2000/svg"
    class="svg-icon"
  >
    <component :is="icon"></component>
  </svg>
</template>

<script lang="ts">
import { computed, defineComponent, type Component } from 'vue';
import OwlIcon from './OwlIcon.vue';

const icons: { [key: string]: Component } = {
  owlIcon: OwlIcon
};

export default defineComponent({
  name: 'IconComponent',
  props: {
    viewBox: {
      type: String,
      default: '0 0 24 24'
    },
    width: {
      type: String,
      default: '24'
    },
    height: {
      type: String,
      default: '24'
    },
    type: {
      type: String,
      required: true
    }
  },
  setup(props) {
    const icon = computed(() => icons[props.type]);

    return { icon };
  }
});
</script>
