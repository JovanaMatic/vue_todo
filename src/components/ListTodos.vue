<template>
  <div class="todos">
    <ul v-if="this.todos">
      <li ref="todo" v-for="todo in todos" :key="todo">{{ todo }}<span @click="checkTodo($event)">&#10003;</span></li>
    </ul>
    </div>
    <div class="todo-buttons">
       <delete-todos @delete-all="deleteAllTodos"></delete-todos>
    </div>
</template>

<script>
import DeleteTodos from './DeleteTodos.vue'

  export default {
    components: {
      DeleteTodos
    },
    props: ['todos'],
    emits:['delete-all'],
    data() {
      return {
        isChecked: false,
      }
    },
    methods: {
      deleteAllTodos() {
        this.$emit('delete-all')
      },
      checkTodo(e) {
        e.target.parentElement.classList.toggle('check')
      }
    }
  }
</script>

<style scoped>
  .todo-buttons {
    display: flex;
    justify-content: start;
  }

  ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }

  li {
    padding: 10px;
    margin: 20px;
    text-transform: uppercase;
    width: 400px;
    border-bottom: 1px solid rgba(37, 117, 208, 0.351);
    cursor: pointer;
  }

  li:hover {
    color: rgba(37, 117, 208, 0.397);
  }
  .check {
  text-decoration: line-through;
  }

  span {
    float: right;
    cursor: pointer;
  }

  .container h2 {
    color: rgb(245, 46, 208)
  }
</style>