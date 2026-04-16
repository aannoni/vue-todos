<script setup>
import { reactive, defineEmits } from "vue";
import TodoButton from "./TodoButton.vue";

const emit = defineEmits(["created-todo"]);

const inputState = reactive({
  todo: "",
  invalid: null,
  errorMessages: "",
})

const createTodo = () => {
  inputState.invalid = null;
  if (inputState.todo !== "") {
    emit("created-todo", inputState.todo);
    inputState.todo = "";
    return;
  }
  inputState.invalid = true;
  inputState.errorMessages = "Todo cannot be empty"
}
</script>

<template>
  <div class="input-wrap" :class="{ 'input-error': inputState.invalid }">
    <input type="text" v-model="inputState.todo" />
    <TodoButton @click="createTodo()" />
  </div>
  <p v-show="inputState.invalid" class="error-message">{{ inputState.errorMessages }}</p>
</template>

<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;

  &.input-error {
    border-color: red;
  }

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
}

.error-message {
  margin-top: 6px;
  font-size: 12px;
  text-align: center;
  color: red;
}

</style>