<template>
  <div
    class="todo-item"
    :class="{'is-complete': todoItem.completed}"
  >
    <p>{{todoItem.title}}</p>
  </div>
</template>
<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class TodoItem extends Vue {
  @Prop() private todoItem: any;
}
</script>




<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
.is-complete {
  text-decoration: line-through;
}
.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  cursor: pointer;
  float: right;
}
</style>
