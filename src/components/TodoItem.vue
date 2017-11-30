<template>
  <div class="todo">
    <div class="content" v-show="!isEditing">
      <span class="title">{{ todo.title }}</span>
      <button type="button" class="btn btn-secondary btn-sm" @click="showForm()">Edit</button>
      <button type="button" class="btn btn-danger btn-sm" @click="deleteTodo()">remove</button>
    </div>
    <div class="content" v-show="isEditing">
      <div class="ui form">
        <div class="field">
          <label for="title">Title</label>
          <input id="title" type="text" v-model="todo.title" >
        </div>
        <div class="ui two button attached buttons">
          <button class="ui basic blue button" @click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>

    <button type="button" class="btn btn-success btn-block" v-show="!isEditing && todo.done" @click="completeTodo()">Mark pending</button>
    <button type="button" class="btn btn-secondary btn-block" v-show="!isEditing && !todo.done" @click="completeTodo()">Mark completed</button>
  </div>
</template>

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

<style scoped>
  .todo {
    margin-bottom: 10px;
  }

  .content {
    border: 1px solid #dfdfdf;
    border-radius: 4px;
  }
</style>
