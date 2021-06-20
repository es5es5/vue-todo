<template>
  <div>
    <label for="todo-input">오늘 할 일 :</label>
    <input type="text" name="todo-input" id="todo-input" :value="item" @input="handleInput">
    <button type="button" @click="addTodo">add</button>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'

  export default Vue.extend({
    name: 'TodoInput',
    props: {
      item: {
        type: String,
        required: true,
      }
    },
    methods: {
      addTodo () {
        this.$emit('add')
      },
      handleInput (event: InputEvent) {
        console.log(event)
        if (event.target) {
          const eventTarget = event.target as HTMLInputElement
          this.$emit('input', eventTarget.value)
        } else {
          return
        }
      }
    }
  })
</script>

<style scoped>

</style>