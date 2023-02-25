<script>
import ButtonElement from './UI/ButtonElement.vue';

export default {
  components: {
    ButtonElement,
  },

  inject: ['storedResources'],

  data() {
    return {};
  },

  emits: ['delete-resource-event'],

  methods: {
    emitDeleteEvent(resourceId) {
      this.$emit('delete-resource-event', resourceId);
    },
  },
};
</script>

<template>
  <ul class="container resource-list" v-if="storedResources.length > 0">
    <li
      class="resource-list__item"
      v-for="resource in storedResources"
      :key="resource.id"
    >
      <base-card class="resource__card">
        <template v-slot:cardContent>
          <h2 class="resource__heading">
            {{ resource.name }}
          </h2>

          <div class="resource__info">
            <p class="resource__description">
              {{ `Description: ${resource.description}` }}
            </p>

            <a target="_blank" class="resource__link" :href="resource.link">
              {{ 'View Resource' }}
            </a>
          </div>

          <button-element
            @click="emitDeleteEvent(resource.id)"
            button-text="Delete Resource"
            class="button--resource-delete"
          ></button-element>
        </template>
      </base-card>
    </li>
  </ul>
</template>

<style scoped>
.resource-list {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 3rem;
  align-items: center;
  margin-top: 5rem;
  margin-bottom: 5rem;
}

.resource-list__item {
  width: 100%;
}

.resource__card {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
  padding: 1rem;
  height: 100%;
  width: 100%;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

.resource__info {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: 75%;
}

.resource__heading {
  text-transform: uppercase;
  font-size: 3.5rem;
  font-weight: 400;
  color: rgb(62, 136, 182);
}

.resource__description {
  font-family: sans-serif;
  font-size: 2.5rem;
  width: 100%;
}

.resource__link {
  color: brown;
  font-size: 2rem;
  transition: all 200ms ease-out;
}

.resource__link:hover {
  font-size: 2rem;
  transform: translateY(-20%);
  transform-origin: left;
  color: black;
}

.button--resource-delete {
  transform: translateY(10%);
  box-shadow: 0 0 5px 0 darkgray inset;
  position: absolute;
  right: 0%;
  bottom: 10%;
}

.button--resource-delete {
  transform: translateY(0%);
}
</style>

<!-- I'll be an immortal. Top of the top. There'll be none better. 
They'll talk about me from now till ubiquitously -->
