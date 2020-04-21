<template>
  <div classs="todo-list">
    <h1>Todo List</h1>
    <div v-bind:key="todo.id" v-for="todo in todos">
      <Todos v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import Todos from '../components/Todos.vue'
export default {
  name: 'TodoList',
  components: {
    Todos
  },
  props: ["todos"]
}
</script>

<style scoped>
  .todo-list {
    width: 100%;
    height: fit-content;
    display: flex;
    flex-direction: column;
    margin: 20px;
  }

  h1 {
    font-size: 22px;
    font-weight: 600;
    color: #e4e4e4;
    text-align: left;
    margin-left: 20px;
  }
</style>