<template>
  <li>
    <slot name="pre-icon" v-bind:value="value"></slot>
    <span v-if="del">{{ title }}</span>
    <span v-else style="text-decoration: line-through;">{{ title }}</span>
    <slot name="suf-icon">默认图标</slot>
    <button v-show="del" v-on:click="handleClick">删除</button>
  </li>
</template>

<script>
export default {
  props: {
    title: String,
    del: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      value: Math.random()
    }
  },
  methods: {
    handleClick () {
      console.log('点击了删除按钮')
      this.$emit('delete', this.title)
    }
  }
}
</script>
