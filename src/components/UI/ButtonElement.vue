// Component containing code related to button

<script>
export default {
  data() {
    return {};
  },

  props: {
    buttonText: {
      type: String,
      required: true,
      validator: function (value) {
        return value.length > 0;
      },
    },
  },
};
</script>

// Like Data, Props are also set on global object.

<template>
  <button>{{ buttonText }}</button>
</template>

<style scoped></style>
