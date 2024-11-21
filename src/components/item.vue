<template>
  <div class="todo-item">
    <div>{{ todo.content }}</div>
    <button @click="deleteTodo">Удалить</button>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
    },
  },
  methods: {
    deleteTodo() {
      this.$emit("del", this.todo.id);
    },
  },
};
</script>

<style scoped>
.todo-item {
  color:black;
  text-shadow: 0 0 3px #e2e7d5;
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin: 20px 0;
  padding: 5px;
  position: relative;
  font-size: 24px;
  border-bottom: 3px solid black;
  
}
</style>
