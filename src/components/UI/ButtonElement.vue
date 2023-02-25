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
  <button class="my-button">{{ buttonText }}</button>
</template>

<style scoped>
.my-button {
  background: none;
  border-radius: 5px;
  border: none;
  color: black;
  cursor: pointer;
  font-family: cursive;
  font-size: 2rem;
  font-style: italic;
  margin-right: 2rem;
  max-width: 22rem;
  outline: none;
  padding: 2vh 2vw;
  text-align: center;
  transition: all 200ms ease-out;
}

.my-button:hover {
  transform: scale(1.05);
  background: lightblue;
  box-shadow: 0.5px 0.5px 1px gray;
}

.my-button:focus {
  outline: none;
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

.button--add {
  font-size: 2.5rem;
  box-shadow: 0.5px 0.5px 5px lightgrey inset;
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
