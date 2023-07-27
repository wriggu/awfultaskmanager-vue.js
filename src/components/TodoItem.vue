<script setup>
import { Icon } from "@iconify/vue";
import { ref } from 'vue';

const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
  index: {
    type: Number,
    required: true,
  },
});
defineEmits(["toggle-complete", "edit-todo", "update-todo", "delete-todo"]);
const inputField = ref() //this doesnt work - fix later
const focusInput = () => {
  inputField.value.focus();
};
</script>

<template>
  <li>
    <input
      type="checkbox"
      :checked="todo.isCompleted"
      @input="$emit('toggle-complete', index)"
    />
    <div class="todo">
      
      <input

        v-if="todo.isEditing"
        type="text"
        :value="todo.todo"
        @input="$emit('update-todo', $event.target.value, index)"
        @keyup.enter="$emit('edit-todo', index)"
      />
      <span v-else :class="{ 'completed-todo': todo.isCompleted }">
        {{ todo.todo }}
      </span>
    </div>
    <div class="todo-actions">
      <Icon
        v-if="todo.isEditing"
        icon="ph:check-circle"
        class="icon"
        color="191815"
        width="22"
        @click="$emit('edit-todo', index)"
      />
      <Icon
        v-else
        icon="ph:pencil-fill"
        class="icon"
        color="191815"
        width="22"
        @click="$emit('edit-todo', index), focusInput()"
          ref="inputField"
      />
      <Icon
        icon="ph:trash"
        class="icon"
        color="#191815"
        width="22"
        @click="$emit('delete-todo', todo.id)"
      />
    </div>
  </li>
</template>

<style lang="scss" scoped>
@keyframes listElementSlide{
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
@keyframes opacitySwitch{
  0% {
    opacity: 0;
  }
  75% {
    opacity: 60%;
  }
  100% {
    opacity: 1;
  }
}

li {
  display: flex;
  align-items: center;
  margin-right: 9%;
  gap: 10px;
  padding: 16px 10px;
  border-radius: 5px;
  background-color: transparent;
  box-shadow: 0 -10px 120px -25px rgb(0 0 0 / 0.1),
    0 8px 25px 1px rgb(0 0 0 / 0.1);
  transition: all .55s ease;
  animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0s 1 listElementSlide;
  &:hover {
    .todo-actions {
      opacity: 1;
    }
    transform: scale(1.05);
    
  }

  input[type="checkbox"] {
    appearance: none;
    width: 20px;
    height: 20px;
    background-color: 191815;
    border: 1px solid #191815;
    border-radius: 50%;
    box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
    cursor: pointer;

    &:checked {
      background-color: #191815;
      transition: 150ms ease-in-out;
    }
  }

  .todo {
    flex: 1;
      animation: 1s cubic-bezier(0.14, 0.93, 0.6, 1.01) 0s 1 listElementSlide;
    .completed-todo {
      text-decoration: line-through;
      color: #191815;
    }

    input[type="text"] {
      border: transparent;
      width: 100%;
      
      &:focus {
      outline: none;
      }
    }
  }

  .todo-actions {
    display: flex;
    gap: 6px;
    opacity: 0;
    transition: 150ms ease-in-out;

    .icon {
      background-color: transparent;
      cursor: pointer;
    }
  }
}
</style>
