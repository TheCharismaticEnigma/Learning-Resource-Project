<!-- Responsible for displaying an error message -->
<!-- Dynamically gets content for  -->

<script>
import ButtonElement from './UI/ButtonElement.vue';

export default {
  components: {
    ButtonElement,
  },

  data() {
    return {};
  },

  emits: ['restore-component-event'],

  methods: {
    restoreComponent() {
      // Emit a custom event.
      this.$emit('restore-component-event');
    },
  },
};
</script>

<template>
  <div class="overlay">
    <base-card class="error__card">
      <template v-slot:cardContent>
        <div class="error__content" on>
          <h2 class="error__title">INVALID INPUT!</h2>
          <p class="error__message error__message-first">
            Unfortunately,at lease one input is invalid!
          </p>
          <p class="error__message error__message-second">
            Please check all inputs and make sure you enter at least a few
            characters into each input field.
          </p>
        </div>

        <button-element
          @click="restoreComponent"
          button-text="Try Again"
          class="error__button"
        ></button-element>
      </template>
    </base-card>
  </div>
</template>

<style scoped>
#app-body {
  position: relative;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;

  background-image: linear-gradient(
    120deg,
    rgba(0, 0, 0, 0.5),
    rgba(0, 0, 0, 0.3),
    rgba(0, 0, 0, 0.7)
  );

  backdrop-filter: blur(2px);
  z-index: 999;
}

.error__card {
  min-height: 70vh;
  height: fit-content;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
  justify-content: space-around;
  align-items: center;
  background: wheat;
  border: 2px solid rgba(0, 0, 0, 0.5);
}

.error__content {
  width: 95%;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3rem;
}

.error__title {
  color: brown;
  font-size: 5rem;
  font-weight: 400;
  font-style: italic;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

.error__message {
  line-height: 1.5;
  font-size: 3rem;
  text-align: center;
  text-transform: capitalize;
  font-family: cursive;
}

.error__message-first {
  font-size: 3rem;
  text-transform: uppercase;
  letter-spacing: 1.2px;
}

.error__message-second {
  font-size: 3rem;
}

.error__button {
  box-shadow: 0 0 4px gray inset;
  color: black;
  width: max(25%, 25rem);
}

.error__button:hover {
  background: rgb(19, 4, 4);
  color: wheat;
}
</style>
