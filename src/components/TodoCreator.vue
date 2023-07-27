<script setup>
import { reactive, defineEmits } from "vue";
import TodoButton from "./TodoButton.vue";

const emit = defineEmits(["create-todo"]);

const todoState = reactive({
  todo: "",
  invalid: null,
  errMsg: "",
});

const createTodo = () => {
  todoState.invalid = null;
  if (todoState.todo !== "") {
    emit("create-todo", todoState.todo);
    todoState.todo = "";
    return;
  }
  todoState.invalid = true;
  todoState.errMsg = "Enter a task";
};
</script>

<template>
  <div class="input-wrap" :class="{ 'input-err': todoState.invalid }">
    <input type="text" v-model="todoState.todo" v-on:keyup.enter="createTodo()" autofocus />
    <TodoButton @click="createTodo()" />
  </div>
  <p v-show="todoState.invalid" class="err-msg">{{ todoState.errMsg }}</p>
</template>

<style lang="scss" scoped>
.input-wrap {
  padding-left: 5px;
  display: flex;
  transition: 250ms ease;
  border: 2px solid #191815;
  background-color: #e8e8cf;

  &.input-err {
    border-color: #FF6961;
  }

  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;
    background-color: #e8e8cf;

    &:focus {
      outline: none;
    }
  }
}

.err-msg {
  margin-top: 6px;
  margin-bottom: -18px;
  font-size: 12px;
  text-align: center;
  color: #FF6961;
}
</style>
