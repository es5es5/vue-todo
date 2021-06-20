<template>
  <div>
    <label for="todo-input"></label>
    <input type="text" name="todo-input" id="todo-input">
    <button type="button" @click="addTodo">add</button>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'

  export default Vue.extend({
    methods: {
      addTodo () {
        console.log('Add')
      }
    }
  })
</script>

<style scoped>

</style>