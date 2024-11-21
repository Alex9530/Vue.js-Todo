<template>
  <section class="real-app">
    <input 
      type="text"
      class="add-input"
      autofocus="autofocus"
      placeholder="Введите задачу + Enter"
      v-on:keyup.enter="addTodo" />

    <Item
      v-for="todo in renderTodos"
      :todo="todo"
      :key="todo.id"
      v-on:del="deleteTodo" />
  </section>
</template>

<script>
import Item from "./item.vue";

let id = 0;

export default {
  data() {
    return {
      todos: [],
    };
  },
  components: {
    Item,
  },
  computed: {
    renderTodos() {
      return this.todos;
    },
  },
  methods: {
    addTodo(e) {
      this.todos.unshift({
        id: id++,

        content: e.target.value,
      });

      e.target.value = "";
    },
    deleteTodo(id) {
      this.todos.splice(
        this.todos.findIndex((todo) => id === todo.id),

        1
      );
    },
  },
};
</script>

<style scoped>
.real-app {
  color: #e8e8ed;
  padding: 20px;
  width: 600px;
  margin: 0 auto;
  box-shadow: 0 0 5px #b5e833;
  border-radius: 20px;
}
.add-input {
  color: black;
  background-color: white;
  border: none;
  font-size: 20px;
  border-bottom: 1px solid #fff;
  border-radius: 30px;
  padding: 20px;
  width: 400px;
}
.add-input:hover{
  border: 3px solid black;
}
</style>
