<template>
  <div id="app">
    <Header />
    <AddTodo @add-todo="addTodo" />
    <Todos
      :todos="todos"
      @del-todo="deleteTodo"
    />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import axios from "axios";
import Todos from "./components/Todos.vue";
// import TodoItem from "./components/TodoItem.vue";
import AddTodo from "./components/AddTodo.vue";
import Header from "./components/layout/header.vue";

@Component({
  components: {
    AddTodo,
    Todos,
    Header
  }
})
export default class App extends Vue {
  public todos: any = [];
  responsHandling(respon: any, title: string) {
    if (respon.length === 0) {
      alert("Error no return data");
    }
    if (this.todos.some(todo => todo.title === title)) {
      alert("Todo already exist!");
    } else {
      this.todos = [...this.todos, respon];
    }
  }
  deleteTodo(id: number) {
    axios
      .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => (this.todos = this.todos.filter(todo => todo.id !== id)))
      .catch(err => window.alert(err));
  }
  addTodo(NewTodo) {
    const { title, completed } = NewTodo;
    axios
      .post(`https://jsonplaceholder.typicode.com/todos`, {
        title,
        completed
      })
      .then(res => this.responsHandling(res.data, title))
      .catch(err => window.alert(err));
  }
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => (this.todos = res.data))
      .catch(err => window.alert(err));
  }
}
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
