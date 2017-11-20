<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => todo.done === true).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => todo.done === false).length}}</p>
    <todo-item v-for="todo in todos" :todo="todo" :key="todo.id" @delete-todo="deleteTodo" @complete-todo="completeTodo"/>
  </div>
</template>

<style scoped>
</style>

<script>
  import TodoItem from './TodoItem';

  export default {
    props: {
      todos: Array,
    },
    components: {
      TodoItem,
    },
    methods: {
      deleteTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos.splice(todoIndex, 1);
      },
      completeTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos[todoIndex].done = !this.todos[todoIndex].done;
      },
    },
  };
</script>
