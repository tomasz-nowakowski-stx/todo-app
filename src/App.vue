<template>
  <div>
    <todo-list :todos="todos" />
    <create-todo @add-todo="addTodo" />
  </div>
</template>

<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
  data() {
    return {
      todos: [{
        id: 1,
        title: 'Todo A',
        done: false,
      }, {
        id: 2,
        title: 'Todo B',
        done: true,
      }, {
        id: 3,
        title: 'Todo C',
        done: false,
      }, {
        id: 4,
        title: 'Todo D',
        done: false,
      }],
    };
  },
};
</script>
