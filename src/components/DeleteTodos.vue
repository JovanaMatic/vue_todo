<template>
  <div class="buttons-container">
    <button class="delete" @click="deleteAll">Delete all ToDos</button>
  </div>
</template>

<script>
  export default {
    emits:['delete-all'],
    props: ['isChecked'],
    data() {
      return {
      }
    },
    methods: {
      deleteAll() {
        this.$emit('delete-all')
      }
    }
  }
</script>

<style scoped>


   button {
    background-color: rgb(37, 117, 208);
    border-radius: 5px;
    color:white;
    border: none;
    min-width: 150px;
    height: 50px;
    font-size: 18px;
    margin: 10px;
  }
  .delete {
    background-color: rgb(245, 46, 208);
  }
</style>