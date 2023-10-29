<template>
    <form @submit.prevent="addTodo">
      <label for="todo">Add Todo</label>
      <input type="text" placeholder="Add todo..." v-model="todo" />
      <span @click.prevent="addTodo">+</span>
    </form>
</template>

<script>
export default {
  data() {
    return {
      todo: ''
    }
  },
  methods: {
    addTodo() {
      this.$emit('add-todo', this.todo)
      this.todo = '';
    }
  }
}
</script>

<style scoped>
  .main {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  form {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
  }

  label {
    display: block;
    padding: 10px;
    margin: 10px;
    font-size: 30px;
    color: rgb(245, 46, 208);
    font-weight: bold;
  }

  input {
    display: block;
    margin: 10px;
    padding: 15px;
    min-width: 400px;
  }

  input, p {
    font-size: 20px;
    color: rgb(37, 117, 208);
    border: 1px solid rgb(37, 117, 208);
    border-radius: 5px;
  }

  button {
    background-color: rgb(37, 117, 208);
    border-radius: 5px;
    color:white;
    border: none;
    width: 100px;
    height: 50px;
    font-size: 20px;
    margin-top: 10px;
    margin-bottom: 10px;
  }

  span {
    font-size: 30px;
    position: absolute;
    bottom: 20px;
    right: 20px;
    cursor: pointer
  }

</style>