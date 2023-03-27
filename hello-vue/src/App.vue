<template>
  <todo-list>
    <todo-item v-for='item in list'
               v-bind:key='item.title'
               v-bind:title='item.title'
               v-bind:del='item.del'
               v-on:delete='handleDelete'>
      <template v-slot:pre-icon='{value}'>
        <span>前置图标:{{value}}</span>
      </template>
    </todo-item>
  </todo-list>
</template>

<script>
import TodoList from './components/TodoList.vue'
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'App',
  components: {
    TodoList,
    TodoItem
  },
  data () {
    return {
      message: 'hello world',
      list: [
        { title: '课程1', del: false },
        { title: '课程2', del: false }
      ]
    }
  },
  methods: {
    handleDelete (title) {
      console.log('handle delete :', title)
    }
  }
}
</script>

<style></style>
