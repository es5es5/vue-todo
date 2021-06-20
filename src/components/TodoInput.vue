<template>
  <div>
    <label for="todo-input"></label>
    <input type="text" name="todo-input" id="todo-input" :value="item" @input="handleInput">
    <button type="button" @click="addTodo">add</button>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'

  export default Vue.extend({
    name: 'TodoInput',
    props: [
      'item'
    ],
    methods: {
      addTodo () {
        console.log('Add')
      },
      handleInput (event: any) {
        event.target.value;
        this.$emit('input', event.target.value)
      }
    }
  })
</script>

<style scoped>

</style>