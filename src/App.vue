<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col s12">
        <h1>Vue Todos App</h1>
      </div>
    </div>
    <div class="row">
      <div class="input-field col s12">
        <input id="Todo" type="text" v-model="newTodo">
        <label for="Todo">Todo</label>
      </div>
      <div class="col s12">
        <button class="waves-effect waves-light btn" v-on:click="addTodo">Add Todo</button>
      </div>
    </div>
    <Todos v-bind:todos="todos" v-on:remove-completed="removeCompleted"/>
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Item from "./components/Item";
export default {
  name: "App",
  components: {
    Todos
  },
  data() {
    return {
      newTodo: "",
      todos: []
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: this.todos.length + 1,
        title: this.newTodo,
        completed: false
      });

      this.newTodo = "";
    },
    removeCompleted() {
      console.log("remove todos");
      this.todos = this.todos.filter(todo => !todo.completed);
    }
  },
  created() {
    console.log(111);
    fetch("https://jsonplaceholder.typicode.com/todos")
      .then(response => response.json())
      .then(json => (this.todos = json));
  }
};
</script>

<style>
</style>
