<script setup>
import { ref, reactive } from "vue";

const simple = ref("");

// console.log(simple.value);
// shows me the actual value of simple (like what is inside simple)

const complex = reactive({
  name: "test"
});

// console.log(complex.name);

</script>

<template>
  <!-- ref can only use primitive data types -->
  <div class="input-wrap">
    <input type="text" v-model="simple" />
  </div>
  <p> {{ simple }}</p>

  <!-- reactive for more complex data types -->
  <div class="input-wrap">
    <input type="text" v-model="complex.name" />
  </div>
  <p> {{ complex.name }}</p>

</template>

<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;

  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;

    &:focus {
      outline: none;
    }
  }

  button {
    padding: 8px 16px;
    border: none;
  }
}
</style>