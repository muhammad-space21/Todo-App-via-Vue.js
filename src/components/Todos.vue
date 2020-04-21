<template>
  <div class="todos" v-bind:class="{'completed': todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markCompleted" v-bind:checked="todo.completed">
      {{todo.title}}
      <button class="delete" @click="$emit('del-todo', todo.id)">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: 'Todos',
  props: ["todo"],
  methods: {
    markCompleted() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>
  .todos {
    margin-left: 20px;
    font-size: 14px;
    line-height: 20px;
    color: grey;
  }
  .completed {
    font-style: italic;
    opacity: 0.5;
    text-decoration: line-through;
  }
  .delete {
    background: white;
    color: red;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
    margin-right: 20px;
  }
</style>