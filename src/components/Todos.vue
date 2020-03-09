<template>
  <div class="todos">
    <div
      v-for="todo in todos"
      :key="todo.id"
    >
      <TodoItem
        :todo="todo"
        @del-todo="$emit('del-todo', todo.id)"
      />
    </div>
  </div>
</template>

<script lang="ts">
import TodoItem from "./TodoItem.vue";
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({
  components: {
    TodoItem
  }
})
export default class Todos extends Vue {
  @Prop() public todos: any;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
