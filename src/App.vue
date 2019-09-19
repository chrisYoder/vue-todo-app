<template>
  <div id="app">
    <h1 class="center">Vue.js Todo App</h1>
    <div class="ui divider"></div>

    <todo-list v-bind:todos="todos"/>
    <create-todo v-on:add-todo="addTodo"/>
  </div>
</template>

<script>
import TodoList from "./components/TodoList";
import CreateTodo from "./components/CreateTodo";

export default {
  name: "App",
  components: {
    TodoList,
    CreateTodo
  },

  data() {
    return {
      todos: [
        {
          title: "Todo A",
          project: "Project A",
          done: false
        },
        {
          title: "Todo B",
          project: "Project B",
          done: true
        },
        {
          title: "Todo C",
          project: "Project C",
          done: false
        },
        {
          title: "Todo D",
          project: "Project D",
          done: false
        }
      ]
    };
  },

  methods: {
    addTodo(title) {
      this.todos.push({
        title,
        done: false
      });
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h1 {
  margin-bottom: 0;
  padding-bottom: 0;
}

.divider {
  margin-top: 0;
  padding-top: 0;
}
</style>
