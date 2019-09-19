<template>
  <div class="ui centered card">
    <div class="content" v-show="!isEditing">
      <div class="header">{{ todo.title }}</div>
      <div class="meta">{{ todo.project }}</div>
      <div class="extra content">
        <span class="right floated edit icon" @click="showForm">
          <i class="edit icon"></i>
        </span>
        <span class="right floated trash icon" @click="deleteTodo(todo)">
          <i class="trash alternate icon"></i>
        </span>
      </div>
    </div>
    <!-- end of !isEditing -->
    <div class="content" v-show="isEditing">
      <div class="ui form">
        <div class="field">
          <label>Title</label>
          <input type="text" name="title" v-model="todo.title">
        </div>
        <div class="field">
          <label>Project</label>
          <input type="text" name="project" v-model="todo.project">
        </div>
        <div class="ui two button attached buttons">
          <button class="ui basic blue button" @click="hideForm">Close X</button>
        </div>
      </div>
    </div>

    <div class="ui bottom attached green basic button" v-show="todo.done">Completed</div>
    <div class="ui bottom attached red basic button" v-show="!todo.done">Complete</div>
  </div>
</template>

<script>
export default {
  props: ["todo"],
  data() {
    return {
      isEditing: false
    };
  },
  methods: {
    hideForm() {
      this.isEditing = false;
    },
    showForm() {
      this.isEditing = true;
    }, 
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    }
  }
};
</script>

<style>
</style>
