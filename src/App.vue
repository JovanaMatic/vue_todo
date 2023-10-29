<template>
  <section>
    <header>
      <h1>Todo List</h1>
    </header>
    <div class="main">
      <div class="container">
        <add-todo @add-todo="addTodo"></add-todo>
        <list-todos :todos="todos" @delete-all="deleteAllTodos"></list-todos>
      </div>
    </div>
  </section>
</template>

<script>
import AddTodo from './components/AddTodo.vue'
import ListTodos from './components/ListTodos.vue'

export default {
  components: {
    AddTodo,
    ListTodos,
  },
  data() {
    return {
      todos: [],
    }
  },
  created() {
    this.todos = JSON.parse(localStorage.getItem('todos'));
    if(this.todos === null) {
      this.todos = []
    }
  },
  methods: {
    addTodo(todo) {
      if(todo !== '') {
        this.todos.push(todo);
        localStorage.setItem('todos', JSON.stringify(this.todos))
      }
    },
    deleteAllTodos() {
      this.todos = [];
      localStorage.clear()
    },
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: 'Jost', sans-serif;
}
body {
  margin: 0;
  color: rgb(37, 117, 208)
}

header {
  padding: 15px;
  color: white;
  background-color: rgb(37, 117, 208);
}

.main {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    color: rgb(37, 117, 208);
    font-size: 20px;
    flex-direction: column;
  }
  .container {
    min-height: 100px;
    min-width: 500px;
    box-shadow: 5px 5px 10px rgba(37, 117, 208, 0.444);
    margin-top: 30px;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

</style>