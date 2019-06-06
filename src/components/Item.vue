<template>
  <li
    class="collection-item"
    v-bind:class="{'active': todo.completed === true}"
    v-on:click="markCompleted"
  >{{todo.title}}</li>
</template>

<script>
export default {
  name: "Item",
  props: ["todo"],
  methods: {
    markCompleted() {
      console.log("mark");
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style>
.active label {
  text-decoration: line-through;
  color: #fff;
}
</style>
