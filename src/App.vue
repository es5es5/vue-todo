<template>
  <div id="app">
    <TodoInput :item="todoText" @input="updateTodoText" @add="addTodoItem" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import TodoInput from './components/TodoInput.vue';

export default Vue.extend({
  name: 'App',
  components: {
    TodoInput
  },
  data () {
    return {
      todoText: ''
    }
  },
  methods: {
    updateTodoText (value: any) {
      this.todoText = value;
    },
    addTodoItem () {
      const value = this.todoText
      localStorage.setItem(value, value)
      this.initTodoText()
    },
    initTodoText () {
      this.todoText = ''
    }
  }
});
</script>

<style>
</style>
