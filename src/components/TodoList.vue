<template>
  <div class="center">
    <p>Completed Tasks: {{ todos.filter(todo => {return todo.done === true}).length }}</p>
    <p>Pending Tasks: {{ todos.filter(todo => { return todo.done === false}).length }}</p>
    <todo v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:todo="todo"/>
  </div>
</template>

<script>
import Todo from "./Todo";

export default {
  props: ["todos"],
  components: {
    Todo
  },

  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    }
  }
};
</script>
<style>
.center {
  text-align: center;
}
</style>
