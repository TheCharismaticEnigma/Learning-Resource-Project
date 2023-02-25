// Component responsible for rendering/styling/behavior // of buttonContainer

<script>
import ButtonElement from './UI/ButtonElement.vue';

export default {
  name: 'ButtonContainer',

  components: {
    ButtonElement,
  },

  data() {
    return {
      selectedButton: '',
    };
  },

  emits: ['change-component'],

  methods: {
    toggleComponent(componentName) {
      // Emit a custom event to send data to the parent
      this.$emit('change-component', componentName);
    },
  },
};
</script>

<template>
  <base-card class="button-card-wrapper">
    <template v-slot:cardContent>
      <div class="container button-container">
        <button-element
          v-on:click="toggleComponent('ResourceContainer')"
          button-text="Stored Resources"
        >
        </button-element>

        <button-element
          v-on:click="toggleComponent('AddResource')"
          button-text="Add Resource"
        ></button-element>
      </div>
    </template>
  </base-card>
</template>

<style scoped>
.button-card-wrapper {
  margin-bottom: 5rem;
}

.button-container {
  display: flex;
  align-items: center;
  gap: 2rem;
  height: 15vh;
  padding: 1rem;
  width: 100%;
}
</style>
