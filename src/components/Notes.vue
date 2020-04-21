<template>
  <div class="note-component">
    <div class="note-body">
      <h1>{{title}}</h1>
      <AddTodo v-on:add-todo="addTodo" />
      <TodoList v-bind:todos="todos" v-on:del-todo="deleteTodo" />
      <span class="x_btn" @click="onExit">X</span> 
    </div>
  </div>
</template>

<script>
import TodoList from '../components/TodoList.vue'
import axios from 'axios'
import AddTodo from '../components/AddTodos'

export default {
  props: ['title'],
  name: 'Notes',
  components: {
    TodoList,
    AddTodo
  },
  data() {
    return {
      todos: [],
      notes: []
    }
  },
  methods: {
    onExit() {
      this.$emit("close");
    },
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        // eslint-disable-next-line no-unused-vars
        .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=4')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  }
}
</script>

<style scoped>
  .note-component {
    width: 450px;
    height: fit-content;
    border-radius: 30px;
    background: #46d6ff;
    box-shadow:  20px 20px 60px #3cb6d9, 
                -20px -20px 60px #51f6ff;
  }

  .note-body {
    position: relative;
    width: 100%;
    height: 100%;
  }

  h1 {
    font-size: 25px;
    color: white;
    margin-top: 20px;
    margin-bottom: 20px; 
    text-align: center;
  }
  .x_btn {
    position: absolute;
    top: 0;
    right: 0;
  }
</style>