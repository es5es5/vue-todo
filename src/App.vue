<template>
  <div id="app">
    <TodoInput
      :item="todoText"
      @input="updateTodoText"
      @add="addTodoItem"
    />
    <div>
      <ul>
        <TodoListItem
          v-for="(item, index) in todoItems" :key="index"
          :todoItem="item"
          :index="index"
          @toggle="toggleItem"
          @remove="removeItem"
        />
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import TodoInput from './components/TodoInput.vue'
import TodoListItem from './components/TodoListItem.vue'

const STORAGE_KEY = 'vue-todo-ts-v1'
const storage = {
  save (todoItems: any[]) {
    const parsed = JSON.stringify(todoItems)
    localStorage.setItem(STORAGE_KEY, parsed)
  },
  fetch () {
    const todoItems = localStorage.getItem(STORAGE_KEY) || '[]'
    const result = JSON.parse(todoItems)
    return result
  }
}

export interface TodoItem {
  title: string;
  done: boolean;
}

export default Vue.extend({
  name: 'App',
  created () {
    this.fetchTodoItems()
  },
  components: {
    TodoInput,
    TodoListItem
  },
  data () {
    return {
      todoText: '',
      todoItems: [] as TodoItem[],
    }
  },
  methods: {
    updateTodoText (value: string) {
      this.todoText = value;
    },
    addTodoItem () {
      const value = this.todoText
      const todo: TodoItem = {
        title: value,
        done: false
      }
      this.todoItems.push(todo)
      storage.save(this.todoItems)
      // localStorage.setItem(value, value)
      this.initTodoText()
    },
    initTodoText () {
      this.todoText = ''
    },
    fetchTodoItems () {
      this.todoItems = storage.fetch()
    },
    removeItem (index: number) {
      this.todoItems.splice(index, 1)
      storage.save(this.todoItems)
    },
    toggleItem (item: TodoItem, index: number) {
      this.todoItems.splice(index, 1, {
        ...item,
        done: !item.done
      })
      storage.save(this.todoItems)
    }
  }
});
</script>

<style>
</style>
