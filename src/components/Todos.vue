<template>
  <div class="row" v-if="todos.length > 0">
    <div class="col s12">
      <ul class="collection">
        <Item v-bind:todo="todo" v-for="todo in todos" v-bind:key="todo.id"/>
      </ul>
      <a
        class="waves-effect waves-light btn-small right"
        @click="$emit('remove-completed')"
      >Remove completed</a>
    </div>
  </div>
</template>

<script>
import Item from "./Item";
export default {
  name: "Todos",
  components: {
    Item
  },
  props: ["todos"]
};
</script>
