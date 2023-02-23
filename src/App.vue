<!-- Main App component/Root Component. -->

<script>
export default {
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          name: 'Official Guide',
          description: 'The Official Vue.js Documentation.',
          link: 'https://vuejs.org',
        },

        {
          id: 'google',
          name: 'Google',
          description: 'Google that bitch! AHAHAHAHA! .',
          link: 'https://www.google.com',
        },
      ],
    };
  },
};
</script>

<template>
  <ul v-if="storedResources.length > 0">
    <li v-for="resource in storedResources" :key="id">
      <h2>{{ resource.name }}</h2>
      <p>{{ resource.description }}</p>
      <a :href="resource.link"> {{ resource.link }} </a>
    </li>
  </ul>
</template>

<!-- This contains GLOBAL APP STYLES -->

<style></style>
