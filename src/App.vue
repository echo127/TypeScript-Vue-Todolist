<template>
  <div id="app">
    <Todos :todos="todos" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Todos from "./components/Todos.vue";

@Component({
  components: {
    Todos
  },
  data() {
    return {
      todos: [
        { id: 1, title: "Todo One", completed: true },
        { id: 2, title: "Todo Two", completed: false },
        { id: 3, title: "Todo Three", completed: false }
      ]
    };
  }
})
export default class App extends Vue {}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
