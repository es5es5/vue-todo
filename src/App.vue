<template>
  <div id="app">
    <TodoInput />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import TodoInput from './components/TodoInput.vue';

export default Vue.extend({
  name: 'App',
  components: {
    TodoInput
  }
});
</script>

<style>
</style>
