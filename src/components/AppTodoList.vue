<template>
  <ul class="todo-list">
    <AppTodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-todo="toggleTodo"
      @remove-todo="removeTodo"
    />
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
  },
  methods: {
    toggleTodo(id: number) {
      const targetTodo = this.todos.find((todo: Todo) => todo.id === id)

      if (targetTodo) {
        targetTodo.completed = !targetTodo.completed
      }
    },
    removeTodo(id: number) {
      // отфильтрованный массив из которого удаляем задачу id которой получили
      this.todos = this.todos.filter((todo: Todo) => todo.id !== id)
    }
  }
})
</script>