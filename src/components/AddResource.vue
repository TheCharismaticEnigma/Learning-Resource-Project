<!-- component related to the addition of a new resource  -->
<!-- Wrap it around by a card component -->

<script>
import ButtonElement from './UI/ButtonElement';
import ErrorContainer from './ErrorContainer.vue';

export default {
  name: 'AddResource',

  components: {
    ButtonElement,
    ErrorContainer,
  },

  props: {},

  data() {
    return {
      displayError: false,
    };
  },

  emits: ['add-new-resource'],

  methods: {
    createResource() {
      const resourceTitle = this.$refs.titleInput.value;
      const resourceDescription = this.$refs.descriptionInput.value;
      const resourceLink = this.$refs.resourceLinkInput.value;

      if (!resourceTitle || !resourceDescription || !resourceLink) {
        this.displayError = true;
        window.scrollTo(0, 0); // scroll to the top of the window
        return;
      }

      const newResource = {
        id: resourceTitle.toLowerCase(),
        name: resourceTitle,
        description: resourceDescription,
        link: resourceLink,
      };

      // Reset Inputs

      for (const key of Object.keys(this.$refs)) this.$refs[key].value = '';

      // Emit a custom event and then listen to its data value.
      this.$emit('add-new-resource', newResource);
    },

    unrenderErrorMessage() {
      this.displayError = false;
    },
  },
};
</script>

<template>
  <base-card class="form-card">
    <template v-slot:cardContent>
      <form class="resource-form" v-on:submit.prevent>
        <div class="form__group input-title-group">
          <label for="title" class="form__label">Title</label>

          <input
            class="form__input"
            type="text"
            id="title"
            name="title"
            autocomplete="off"
            spellcheck="false"
            ref="titleInput"
          />
        </div>

        <div class="form__group input-description-group">
          <label for="description" class="form__label"> Description </label>

          <input
            class="form__input"
            type="text"
            id="description"
            name="description"
            autocomplete="off"
            spellcheck="false"
            ref="descriptionInput"
          />
        </div>

        <div class="form__group input-link-group">
          <label for="resourceLink" class="form__label"> Resource Link </label>

          <input
            class="form__input"
            type="url"
            id="resourceLink"
            name="resourceLink"
            autocomplete="off"
            spellcheck="false"
            ref="resourceLinkInput"
          />
        </div>

        <button-element
          @click="createResource"
          button-text="Add Resource"
          class="button--add"
        >
        </button-element>
      </form>
    </template>
  </base-card>

  <teleport to="#app-body">
    <error-container
      v-on:restore-component-event="unrenderErrorMessage"
      v-if="displayError"
    >
    </error-container>
  </teleport>
</template>

<style scoped>
.form-card {
  height: fit-content;
  margin-bottom: 5rem;
}

.resource-form {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  gap: 3rem;
  border-radius: inherit;
  height: 100%;
  min-height: 70vh;
  padding: 2rem 1rem;
}

.form__group {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  padding: 0.5rem;
}

.form__label {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 2.5rem;
  font-weight: 600;
}

.form__input {
  padding: 1rem 0.5rem;
  font-size: 2.5rem;
  font-weight: 600;
  box-shadow: 0px 0px 3px rgb(138, 185, 185);
  border: 1px solid transparent;
  border-radius: 5px;
}

.form__input:focus {
  outline: none;
  border: 1px solid black;
}

.button--add {
  font-size: 2.5rem;
  box-shadow: 0.5px 0.5px 5px lightgrey inset;
}
</style>
