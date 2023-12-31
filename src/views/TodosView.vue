<script setup>
import { ref, watch, computed } from "vue";
import { uid } from "uid";
import { Icon } from "@iconify/vue";
import TodoCreator from "../components/TodoCreator.vue";
import TodoItem from "../components/TodoItem.vue";
const todoList = ref([]);

watch(
  todoList,
  () => {
    setTodoListLocalStorage();
  },
  {
    deep: true,
  }
);

const todoCompleted = computed(() => {
  return todoList.value.every((todo) => todo.isCompleted);
});

const fetchTodoList = () => {
  const savedTodoList = JSON.parse(localStorage.getItem("todoList"));
  if (savedTodoList) {
    todoList.value = savedTodoList;
  }
};

fetchTodoList();

const setTodoListLocalStorage = () => {
  localStorage.setItem("todoList", JSON.stringify(todoList.value));
};

const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: null,
    isEditing: null,
  });
};

const toggleTodoComplete = (todoPos) => {
  todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
};

const toggleEditTodo = (todoPos) => {
  todoList.value[todoPos].isEditing = !todoList.value[todoPos].isEditing;
};

const updateTodo = (todoVal, todoPos) => {
  todoList.value[todoPos].todo = todoVal;
};

const deleteTodo = (todoId) => {
  todoList.value = todoList.value.filter((todo) => todo.id != todoId);
};
</script>

<template>
  <main>
    <h1>display: task;</h1>
    <TodoCreator @create-todo="createTodo" />
    <ul class="todo-list" v-if="todoList.length > 0">
      <TodoItem
        v-for="(todo, index) in todoList"
        :todo="todo"
        :index="index"
        @toggle-complete="toggleTodoComplete"
        @edit-todo="toggleEditTodo"
        @update-todo="updateTodo"
        @delete-todo="deleteTodo"
      />
    </ul>
    <p class="todos-msg" v-else>
      <Icon icon="fluent-emoji:stopwatch" width="22" />
      <span style="animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0s 1 slideInBottom;">lets get to work</span>
    </p>
    <p v-if="todoCompleted && todoList.length > 0" class="todos-msg">
      <Icon icon="fluent-emoji:thumbs-up" />
      <span>good stuff</span>
    </p>
  </main>
</template>

<style lang="scss" scoped>
@keyframes slideInBottom {
  0% {
    transform: translateY(+75%);
    opacity: 0;
  }
  25% {
    opacity: 0;
  }
  75% {
    opacity: 80%;
  }
  100% {
    transform: translateY(0);
    opacity: 100%;
  }
}

main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 13% auto;
  padding: 40px 21px;
  background-color: transparent;
  animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0s 1 slideInBottom;
  h1 {
    font-weight: 700;
    margin-bottom: 6px;
    text-align: left;
    animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0s 1 slideInBottom;
  }

  .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top: 24px;
    gap: 20px;
    animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0s 1 slideInBottom;
  }

  .todos-msg {
    font-weight: 250;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-top: 24px;
  }
}
</style>
