// UI component. Register locally.

<script>
export default {};
</script>

<template>
  <header class="app-header">
    <h1 class="main-heading">Learning Resource Manager</h1>
  </header>
</template>

<style scoped>
.app-header {
  color: whitesmoke;
  background: rgb(128, 173, 201);
  color: rgba(0, 0, 0, 0.8);
  min-height: 15vh;
  height: fit-content;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 3rem;
}

.main-heading {
  font-size: 5rem;
  font-weight: 500;
  color: whitesmoke;
  text-shadow: 0px 0px 5px brown;
  text-transform: capitalize;
  font-style: italic;
  text-align: center;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>
