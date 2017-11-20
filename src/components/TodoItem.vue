<template>
  <div class='ui centered card'>
    <div class='content' v-show="!isEditing">
      <div class='header'>{{ todo.title }}</div>
      <div class='extra content'>
          <span class='right floated edit icon foo' @click="showForm">
            <i class='edit icon'></i>
          </span>
          <span class='right floated trash icon' @click="deleteTodo(todo)">
            <i class='trash icon'></i>
          </span>
      </div>
    </div>
    <div class='content' v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label for="title">Title</label>
          <input id="title" type='text' v-model="todo.title" >
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' @click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    <div class='ui bottom attached green basic button' v-show="!isEditing && todo.done" @click="completeTodo()">
      Completed
    </div>
    <div class='ui bottom attached red basic button' v-show="!isEditing && !todo.done" @click="completeTodo()">
      Pending
    </div>
  </div>
</template>

<style scoped>
  .content .foo {
    cursor: pointer;
  }
</style>

<script>
  export default {
    props: {
      todo: Object,
    },
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
      deleteTodo() {
        this.$emit('delete-todo', this.todo);
      },
      completeTodo() {
        this.$emit('complete-todo', this.todo);
      },
    },
  };
</script>
