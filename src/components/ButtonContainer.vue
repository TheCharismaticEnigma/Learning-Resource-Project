// Component responsible for rendering/styling/behavior // of buttonContainer

<script>
import ButtonElement from './UI/ButtonElement.vue';
export default {
  name: 'ButtonContainer',
  components: {
    ButtonElement,
  },
};
</script>

<template>
  <div class="button-wrapper">
    <button-element></button-element>
    <button-element></button-element>
  </div>
</template>

<style scoped></style>
