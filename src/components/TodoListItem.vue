<template>
  <li>
    <span class="item" :class="todoItem.done ? 'complete' : '' " @click="toggleItem">{{ todoItem.title }}</span>
    <button type="button" @click="removeItem">삭제</button>
  </li>
</template>

<script lang="ts">
import { TodoItem } from '@/App.vue'
import Vue, { PropType } from 'vue'

export default Vue.extend({
  name: 'TodoListItem',
  props: {
    todoItem: Object as PropType<TodoItem>,
    index: Number,
  },
  methods: {
    removeItem () {
      this.$emit('remove', this.index)
    },
    toggleItem () {
      this.$emit('toggle', this.todoItem, this.index)
    }
  }
})
</script>

<style lang="scss" scoped>
.item {
  cursor: pointer;

  &:hover {
    color: cadetblue;
  }

  &.complete {
    text-decoration: line-through;
  }
}
</style>
