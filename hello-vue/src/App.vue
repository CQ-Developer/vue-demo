<template>
  <div id="app">
    {{ message }}
    <input v-model='message'>
    <!-- v-model 只是下面这种方式的简写 -->
    <!-- <input v-bind:value='message' v-on:input='handleInput'> -->
    <input :value='message' @input='handleInput'>
    <todo-list>
      <todo-item v-for='item in list' :key='item.title' :title='item.title' :del='item.del' @delete='handleDelete'>
        <template v-slot:pre-icon='{value}'>
          <span>前置图标:{{value}}</span>
        </template>
      </todo-item>
    </todo-list>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'app',
  components: {
    TodoList,
    TodoItem
  },
  data () {
    return {
      message: 'hello world',
      list: [
        { title: '课程1', del: false },
        { title: '课程2', del: true },
        { title: '课程3', del: false }
      ]
    }
  },
  methods: {
    handleDelete (title) {
      console.log('handle delete :', title)
    },
    handleInput (event) {
      this.message = event.target.value
    }
  }
}
</script>

<style></style>
