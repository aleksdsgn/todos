<template>
  <ul class="todo-list">
    <AppTodoItem v-for="todo in todos" :key="todo.id" :todo="todo" />
  </ul>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import AppTodoItem from './AppTodoItem.vue';
import { Todo } from '@/types/Todo';

interface State {
  todos: Todo[]
}

export default defineComponent({
  components: {
    AppTodoItem,
  },
  data(): State {
    return {
      todos: [
        { id: 0, text: 'Выучить основы Vue', completed: true },
        { id: 1, text: 'Выучить основы Typescript', completed: false },
        { id: 2, text: 'Выложить этот проект', completed: false },
      ]
    }
  }
})
</script>