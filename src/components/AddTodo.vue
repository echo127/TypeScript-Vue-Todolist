<template>
  <div>
    <form @submit="addTodo">
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add todo"
      />
      <input
        type="submit"
        value="Submit"
        class="btn"
      />
    </form>
  </div>
</template>
<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
// import uuid from "uuid";

@Component({
  data() {
    return {
      title: ""
    };
  }
})
export default class AddTodo extends Vue {
  private title = "";
  addTodo(e) {
    if (this.title.length !== 0) {
      e.preventDefault();
      const newTodo = {
        title: this.title,
        completed: false
      };
      //send up to app.vue
      this.$emit("add-todo", newTodo);
      this.title = "";
    } else {
      window.alert("Can not submit empty value, please add todos!");
    }
  }
}
</script>
<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
</style>
